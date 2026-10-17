# System Design Document (SDD)

## Enterprise AI Application Orchestration Platform

**Document Status:** Draft v1  
**Relationship:** Derived from PRD  
**Architecture Style:** Modular service-oriented platform  
**Primary Runtime:** Python  
**Primary API:** REST / OpenAI-compatible  
**Deployment:** Docker Compose → Kubernetes  
**Primary Database:** PostgreSQL  
**Cache / State:** Redis  
**Vector Store:** Qdrant  
**Observability:** OpenTelemetry + Prometheus + Grafana

---

# 1. System Design Goals

The SDD translates the PRD into an implementable architecture.

The system must allow:

```text
Enterprise Application
        │
        ▼
   Unified AI API
        │
        ▼
 Application Runtime
        │
        ├── Workflow
        ├── Routing
        ├── Policy
        ├── Model Execution
        ├── Fallback
        └── Observability
        │
        ▼
 Multiple LLM Providers
```

The design specifically optimizes for:

- Provider independence
    
- Low runtime overhead
    
- Explainable routing
    
- Workflow portability
    
- Horizontal scalability
    
- Strong observability
    
- Enterprise security
    
- Local/self-hosted development
    
- Incremental MVP implementation
    

---

# 2. System Context

```text
                         ┌─────────────────────┐
                         │ Enterprise Users    │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │ Developer Portal    │
                         │ React / Next.js     │
                         └──────────┬──────────┘
                                    │
                                    ▼
┌─────────────────┐       ┌─────────────────────┐
│ Client Apps     │──────►│    API Gateway      │
│ Python / JS     │       │ OpenAI-compatible   │
└─────────────────┘       └──────────┬──────────┘
                                     │
                                     ▼
                         ┌─────────────────────┐
                         │ Application Runtime │
                         └──────────┬──────────┘
                                    │
             ┌──────────────────────┼──────────────────────┐
             ▼                      ▼                      ▼
       Workflow Engine       Routing Engine          Policy Engine
             │                      │                      │
             └──────────────────────┼──────────────────────┘
                                    ▼
                           Provider Adapter Layer
                                    │
              ┌─────────────────────┼─────────────────────┐
              ▼                     ▼                     ▼
           OpenAI                Anthropic             Ollama
              │                     │                     │
              └─────────────────────┼─────────────────────┘
                                    ▼
                               LLM Models
```

---

# 3. Logical Architecture

The platform is divided into six logical layers.

```text
┌───────────────────────────────────────────────┐
│ 1. EXPERIENCE LAYER                           │
│ React / Next.js Dashboard                     │
└───────────────────────┬───────────────────────┘
                        ▼
┌───────────────────────────────────────────────┐
│ 2. API LAYER                                  │
│ API Gateway / OpenAI-Compatible API           │
└───────────────────────┬───────────────────────┘
                        ▼
┌───────────────────────────────────────────────┐
│ 3. APPLICATION ORCHESTRATION                  │
│ Applications / Workflows / Prompts / Agents  │
└───────────────────────┬───────────────────────┘
                        ▼
┌───────────────────────────────────────────────┐
│ 4. AI RUNTIME                                 │
│ Router / Policy / Executor / Fallback         │
└───────────────────────┬───────────────────────┘
                        ▼
┌───────────────────────────────────────────────┐
│ 5. PROVIDER ABSTRACTION                       │
│ OpenAI / Anthropic / Gemini / Ollama / vLLM  │
└───────────────────────┬───────────────────────┘
                        ▼
┌───────────────────────────────────────────────┐
│ 6. INFRASTRUCTURE                             │
│ PostgreSQL / Redis / Qdrant / Telemetry      │
└───────────────────────────────────────────────┘
```

---

# 4. Core Components

## 4.1 API Gateway

### Responsibilities

- Authenticate requests
    
- Resolve tenant/application
    
- Validate request schema
    
- Apply rate limits
    
- Generate request ID
    
- Support streaming
    
- Forward requests to runtime
    

### Endpoints

```text
POST /v1/chat/completions
GET  /v1/models
GET  /v1/applications
POST /v1/workflows/{id}/run
GET  /v1/executions/{id}
```

The most important endpoint is:

```http
POST /v1/chat/completions
```

---

# 5. Application Service

Manages:

```text
Organization
Workspace
Application
Environment
API Key
```

Hierarchy:

```text
Organization
    │
    └── Workspace
          │
          ├── Development
          └── Production
                │
                └── Application
```

Applications should be isolated logically and through authorization.

---

# 6. Model Registry

The Model Registry is the source of truth for available models.

Example model:

```json
{
  "id": "model_01",
  "name": "llama-3.1-70b",
  "provider": "ollama",
  "model_name": "llama3.1:70b",
  "capabilities": [
    "chat",
    "reasoning",
    "tool_calling"
  ],
  "context_window": 128000,
  "input_price": 0,
  "output_price": 0,
  "status": "healthy"
}
```

### Model Registry Responsibilities

- Provider association
    
- Capability metadata
    
- Pricing
    
- Health
    
- Availability
    
- Context limits
    
- Deployment type
    
- Benchmark results
    

---

# 7. Provider Adapter Interface

Every provider implements the same internal contract.

```python
from abc import ABC, abstractmethod

class LLMProvider(ABC):

    @abstractmethod
    async def chat(self, request):
        pass

    @abstractmethod
    async def stream(self, request):
        pass

    @abstractmethod
    async def health_check(self):
        pass

    @abstractmethod
    async def get_model_info(self):
        pass
```

The application runtime should never directly call:

```python
openai.ChatCompletion.create(...)
```

Instead:

```python
provider.chat(request)
```

This is a key architectural boundary.

---

# 8. Provider Adapter Registry

```text
ProviderRegistry
       │
       ├── OpenAIAdapter
       ├── AnthropicAdapter
       ├── GeminiAdapter
       ├── OllamaAdapter
       ├── VLLMAdapter
       └── OpenAICompatibleAdapter
```

Example:

```python
provider = provider_registry.get(
    provider_name="ollama"
)

response = await provider.chat(request)
```

Adding a new provider should not require modifying the workflow engine.

---

# 9. Workflow Engine

The workflow engine executes a platform-neutral workflow graph.

## Workflow

```json
{
  "id": "customer-support",
  "version": 3,
  "nodes": [
    {
      "id": "input",
      "type": "input"
    },
    {
      "id": "retrieve",
      "type": "retrieval"
    },
    {
      "id": "llm",
      "type": "llm",
      "config": {
        "model": "auto"
      }
    },
    {
      "id": "output",
      "type": "output"
    }
  ]
}
```

---

# 10. Workflow Node Types

### MVP

```text
INPUT
PROMPT
LLM
TRANSFORM
CONDITION
OUTPUT
```

### P1

```text
RETRIEVAL
TOOL
PARALLEL
MERGE
HTTP
```

### P2

```text
AGENT
HUMAN_APPROVAL
SUBWORKFLOW
MULTI_AGENT
```

---

# 11. Workflow State

Every execution maintains state.

```python
class WorkflowState:
    execution_id: str
    workflow_id: str
    workflow_version: int
    variables: dict
    node_outputs: dict
    current_node: str
    metadata: dict
```

Example:

```json
{
  "execution_id": "exec_8293",
  "variables": {
    "question": "What is our refund policy?"
  },
  "node_outputs": {
    "retrieve": [...],
    "llm": "Customers can request..."
  },
  "current_node": "output"
}
```

---

# 12. Routing Engine

The routing engine is composed of four stages.

```text
Request
   │
   ▼
Candidate Discovery
   │
   ▼
Policy Filtering
   │
   ▼
Constraint Filtering
   │
   ▼
Scoring
   │
   ▼
Selected Model
```

---

## 12.1 Candidate Discovery

Find models capable of executing the requested workload.

Example:

```text
Required:
chat
tool_calling
context >= 16k
```

Models failing these requirements are excluded.

---

## 12.2 Policy Filtering

Apply:

```text
Organization Policy
Workspace Policy
Application Policy
Workflow Policy
```

Most-specific policy wins, subject to organizational restrictions.

---

## 12.3 Constraint Filtering

Example:

```yaml
max_latency_ms: 3000
max_cost_usd: 0.05
required_context: 16000
```

Models violating hard constraints are removed.

---

## 12.4 Scoring

Remaining candidates are scored.

```python
score = (
    quality_weight * quality
    + reliability_weight * reliability
    + health_weight * health
    - cost_weight * cost
    - latency_weight * latency
)
```

The MVP should use deterministic scoring.

---

# 13. Fallback Engine

The fallback engine operates independently from the primary routing decision.

```text
Primary Model
      │
      ▼
Execution
      │
   ┌──┴──┐
Success Failure
   │      │
   │      ▼
   │   Retry Policy
   │      │
   │      ▼
   │   Fallback Model
   │      │
   │      ▼
   └──► Response
```

Failure categories:

```text
RETRYABLE
NON_RETRYABLE
RATE_LIMIT
TIMEOUT
PROVIDER_UNAVAILABLE
AUTHENTICATION_ERROR
CONTEXT_TOO_LARGE
```

Not every error should trigger fallback.

For example:

```text
Invalid request → no fallback
Provider timeout → fallback
Rate limit → retry/fallback
Provider outage → fallback
```

---

# 14. Policy Engine

The Policy Engine evaluates requests before execution.

Example:

```yaml
policy:
  allowed_models:
    - enterprise-model
    - private-llama

  max_cost_per_request: 0.05

  max_tokens: 8000

  data_classification:
    confidential:
      allowed_providers:
        - private
```

Decision:

```text
ALLOW
DENY
MODIFY
ROUTE
WARN
```

---

# 15. Prompt Service

Prompt management should be version controlled.

```text
Prompt
 ├── v1
 ├── v2
 └── v3
```

A workflow should reference:

```json
{
  "prompt_id": "support-system",
  "version": 3
}
```

rather than copying raw prompt text into every workflow.

This provides reproducibility.

---

# 16. Execution Manager

The Execution Manager coordinates runtime operations.

```text
Execution Manager
       │
       ├── Load Workflow
       ├── Load Prompt
       ├── Evaluate Policy
       ├── Route Model
       ├── Execute
       ├── Retry
       ├── Fallback
       ├── Collect Usage
       └── Emit Telemetry
```

It should be stateless wherever possible.

---

# 17. Data Architecture

## 17.1 Primary Entities

```text
Organization
     │
Workspace
     │
Application
     │
 ┌───┼──────────┬───────────┐
 ▼   ▼          ▼           ▼
Workflow Prompt Agent      Tool
 │
 ▼
WorkflowVersion
 │
 ▼
Execution
 │
 ▼
ModelExecution
```

---

# 18. Proposed PostgreSQL Schema

## organizations

```text
id
name
created_at
updated_at
```

## workspaces

```text
id
organization_id
name
created_at
```

## applications

```text
id
workspace_id
name
description
environment
status
created_at
updated_at
```

## providers

```text
id
name
type
base_url
status
created_at
updated_at
```

## models

```text
id
provider_id
name
external_model_name
context_window
capabilities
input_price
output_price
status
metadata
created_at
updated_at
```

## workflows

```text
id
application_id
name
description
current_version
status
created_at
updated_at
```

## workflow_versions

```text
id
workflow_id
version
definition_json
created_by
created_at
```

## prompts

```text
id
application_id
name
created_at
```

## prompt_versions

```text
id
prompt_id
version
template
variables
created_by
created_at
```

## executions

```text
id
application_id
workflow_id
workflow_version
status
started_at
completed_at
input_tokens
output_tokens
estimated_cost
latency_ms
trace_id
```

## model_executions

```text
id
execution_id
model_id
provider_id
attempt
status
input_tokens
output_tokens
latency_ms
estimated_cost
error_code
started_at
completed_at
```

---

# 19. Redis Architecture

Redis should not be the source of truth.

Use it for ephemeral/high-speed state:

```text
Redis
│
├── Rate Limits
├── Provider Health Cache
├── Model Metadata Cache
├── Execution Locks
├── Short-lived Workflow State
└── Background Job Coordination
```

---

# 20. API Architecture

## 20.1 Chat Completions

```http
POST /v1/chat/completions
```

Request:

```json
{
  "model": "auto",
  "messages": [
    {
      "role": "user",
      "content": "Explain our refund policy."
    }
  ],
  "stream": false
}
```

Response:

```json
{
  "id": "chatcmpl_eaop_123",
  "object": "chat.completion",
  "model": "enterprise-balanced",
  "choices": [
    {
      "index": 0,
      "message": {
        "role": "assistant",
        "content": "..."
      },
      "finish_reason": "stop"
    }
  ],
  "usage": {
    "prompt_tokens": 850,
    "completion_tokens": 320,
    "total_tokens": 1170
  }
}
```

---

# 21. Platform-Specific API

The platform should additionally expose richer EAOP APIs.

### Applications

```http
POST   /api/v1/applications
GET    /api/v1/applications
GET    /api/v1/applications/{id}
PATCH  /api/v1/applications/{id}
DELETE /api/v1/applications/{id}
```

### Models

```http
POST /api/v1/models
GET  /api/v1/models
GET  /api/v1/models/{id}
POST /api/v1/models/{id}/health
POST /api/v1/models/{id}/benchmark
```

### Workflows

```http
POST /api/v1/workflows
GET  /api/v1/workflows
GET  /api/v1/workflows/{id}
POST /api/v1/workflows/{id}/execute
POST /api/v1/workflows/{id}/publish
```

### Executions

```http
GET /api/v1/executions/{id}
GET /api/v1/executions/{id}/trace
```

---

# 22. Benchmarking Architecture

Benchmark jobs should run asynchronously.

```text
Developer
   │
   ▼
POST /benchmarks
   │
   ▼
Job Queue
   │
   ▼
Benchmark Worker
   │
   ├── Model A
   ├── Model B
   └── Model C
   │
   ▼
Results
   │
   ▼
PostgreSQL
```

Benchmark metrics:

```text
Model
Load Time
Prompt Tokens
Output Tokens
Tokens/sec
TTFT
Total Latency
Memory
CPU
GPU
Estimated Cost
Error Rate
```

For cloud models, CPU/GPU metrics may not be available and should be marked accordingly rather than inferred.

---

# 23. Observability Pipeline

```text
Runtime
   │
   ├── Trace
   ├── Metric
   └── Log
   │
   ▼
OpenTelemetry Collector
   │
 ┌─┼──────────────┐
 ▼ ▼              ▼
Tempo Prometheus Loki
 │    │             │
 └────┼─────────────┘
      ▼
   Grafana
```

This provides a vendor-neutral telemetry architecture.

---

# 24. Trace Structure

Example:

```text
trace_id: abc123

Root: API Request
│
├── authentication
│
├── policy_evaluation
│
├── workflow_execution
│   │
│   ├── prompt_node
│   │
│   ├── routing
│   │   ├── candidate_a
│   │   ├── candidate_b
│   │   └── selected_b
│   │
│   └── llm_execution
│       ├── provider
│       ├── model
│       ├── tokens
│       └── latency
│
└── response
```

---

# 25. Security Architecture

## Authentication

MVP:

```text
API Keys
JWT
```

Enterprise:

```text
OIDC
SAML
SSO
```

## Authorization

RBAC:

```text
Administrator
Developer
Viewer
```

Potential future roles:

```text
Platform Engineer
Security Administrator
FinOps Analyst
Auditor
```

---

# 26. Secret Management

Development:

```text
.env
```

Production:

```text
Vault / Cloud Secret Manager
```

Never persist raw provider credentials in application tables.

Instead:

```text
Provider
   │
   └── secret_reference
             │
             ▼
        Secret Manager
```

---

# 27. RAG Architecture

```text
                Documents
                    │
                    ▼
              Ingestion API
                    │
                    ▼
               Parser
                    │
                    ▼
               Chunker
                    │
                    ▼
             Embedding Model
                    │
                    ▼
                 Qdrant
                    │
             ┌──────┴──────┐
             │             │
          Metadata       Vectors
             │             │
             └──────┬──────┘
                    ▼
               Retriever
                    │
                    ▼
                 Prompt
                    │
                    ▼
                   LLM
```

LlamaIndex can be introduced as an adapter around ingestion/retrieval rather than coupling the entire runtime to it.

---

# 28. Deployment Architecture

## MVP Development

```text
┌───────────────────────────────────────┐
│ Docker Compose                        │
│                                       │
│ React                                │
│ FastAPI                              │
│ Worker                               │
│ PostgreSQL                           │
│ Redis                                │
│ Qdrant                               │
│ OpenTelemetry Collector              │
│ Prometheus                            │
│ Grafana                               │
└───────────────────────────────────────┘
```

## Production

```text
                    Internet
                       │
                       ▼
                 Load Balancer
                       │
                       ▼
                  API Gateway
                       │
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼
    Runtime Pod    Runtime Pod    Runtime Pod
        │              │              │
        └──────────────┼──────────────┘
                       │
                 Provider Layer
                       │
       ┌───────────────┼────────────────┐
       ▼               ▼                ▼
    OpenAI          Anthropic         Private
                                     vLLM/Ollama
```

Stateful infrastructure should be independently managed.

---

# 29. MVP Repository Structure

A practical monorepo:

```text
enterprise-ai-orchestrator/
│
├── apps/
│   ├── api/
│   ├── worker/
│   └── web/
│
├── services/
│   ├── routing/
│   ├── workflow/
│   ├── provider/
│   ├── evaluation/
│   └── observability/
│
├── packages/
│   ├── schemas/
│   ├── providers/
│   ├── workflow-ir/
│   ├── routing-engine/
│   └── telemetry/
│
├── infrastructure/
│   ├── docker/
│   ├── kubernetes/
│   └── terraform/
│
├── tests/
│   ├── unit/
│   ├── integration/
│   └── e2e/
│
└── docs/
```

For the initial MVP, several services can remain modules within one FastAPI application rather than immediately becoming independently deployed microservices.

---

# 30. Recommended MVP Architecture

Importantly, **do not start with 15 microservices**.

The first implementation should use a **modular monolith + asynchronous workers**:

```text
                 ┌───────────────────────┐
                 │      FastAPI App      │
                 │                       │
                 │ Application Module    │
                 │ Model Module          │
                 │ Workflow Module       │
                 │ Routing Module        │
                 │ Policy Module         │
                 │ Provider Module       │
                 │ Cost Module           │
                 │ Auth Module           │
                 └──────────┬────────────┘
                            │
                 ┌──────────┼──────────┐
                 ▼          ▼          ▼
             PostgreSQL   Redis      Qdrant
                            │
                            ▼
                     Background Worker
                            │
             ┌──────────────┼──────────────┐
             ▼              ▼              ▼
          Benchmark       Eval          Async Jobs
```

This is substantially easier to develop, test, deploy, and debug.

Services should be extracted into independent deployments **only when scale or ownership boundaries justify it**.

---

# 31. Key Architectural Decisions

|Decision|Choice|Rationale|
|---|---|---|
|Backend|FastAPI/Python|Strong AI ecosystem|
|API|OpenAI-compatible|Lowest adoption friction|
|Database|PostgreSQL|Mature transactional store|
|Cache|Redis|Low-latency ephemeral state|
|Vector DB|Qdrant|Open-source production option|
|Workflow|Platform-neutral graph IR|Avoid UI/framework lock-in|
|Routing|Rule + weighted scoring initially|Explainable|
|Providers|Adapter architecture|Avoid vendor coupling|
|Observability|OpenTelemetry|Vendor neutral|
|Local inference|Ollama|Easy development|
|Production inference|vLLM|High-throughput self-hosting|
|Deployment|Docker → Kubernetes|Progressive complexity|
|Architecture|Modular monolith → services|Avoid premature microservices|

---

# 32. Critical Architecture Boundary

The most important design rule is:

```text
┌─────────────────────────────────────────────┐
│           EAOP CORE IP                      │
│                                             │
│ Application Model                           │
│ Workflow IR                                 │
│ Routing Engine                              │
│ Policy Engine                               │
│ Provider Abstraction                        │
│ Cost/Execution Intelligence                 │
│ Enterprise Analytics                        │
└──────────────────────┬──────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────┐
│        OPEN-SOURCE ECOSYSTEM                │
│                                             │
│ LangGraph │ LlamaIndex │ Qdrant             │
│ Ollama    │ vLLM       │ OpenTelemetry      │
│ Redis     │ PostgreSQL │ Prometheus         │
└─────────────────────────────────────────────┘
```

This prevents the product from becoming merely a repackaged LangChain/LlamaIndex/Dify installation.

The **orchestration intelligence and application runtime** remain the core product.

---

# 33. End-to-End Sequence

The canonical production request is:

```text
Client
 │
 │ POST /v1/chat/completions
 ▼
API Gateway
 │
 │ authenticate
 ▼
Application Service
 │
 │ resolve workflow
 ▼
Workflow Engine
 │
 │ evaluate policy
 ▼
Policy Engine
 │
 │ candidate models
 ▼
Routing Engine
 │
 │ selected model
 ▼
Provider Adapter
 │
 ▼
LLM Provider
 │
 │ response
 ▼
Provider Adapter
 │
 ▼
Workflow Engine
 │
 │ final response
 ▼
API Gateway
 │
 ▼
Client

Meanwhile:

Runtime ─────────► OpenTelemetry
Runtime ─────────► Cost Engine
Runtime ─────────► Usage Store
Runtime ─────────► Audit Log
```

---

## 34. Architecture Readiness

At this point, the project has moved from a **conceptual PRD** to an implementable technical architecture.

The next major specification should be the **MVP Engineering Plan**, structured as:

```text
Phase 0 — Repository + Infrastructure
        ↓
Phase 1 — Identity + Applications
        ↓
Phase 2 — Model Registry + Provider Adapters
        ↓
Phase 3 — OpenAI-Compatible Gateway
        ↓
Phase 4 — Workflow Runtime
        ↓
Phase 5 — Intelligent Routing
        ↓
Phase 6 — Fallback + Reliability
        ↓
Phase 7 — Observability + Cost
        ↓
Phase 8 — Dashboard
        ↓
Phase 9 — Benchmarking + Evaluation
        ↓
Phase 10 — Security Hardening
        ↓
Phase 11 — Docker/Kubernetes Deployment
```

That plan should include **database migrations, API contracts, package structure, implementation order, testing strategy, Docker Compose topology, CI/CD, sample models through Ollama/OpenRouter-compatible endpoints, and concrete deliverables for each phase**.