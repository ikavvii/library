Yes. Now we move from the engineering plan into the **implementation-level contract**: database schema, API contracts, workflow IR, routing policy, and the runtime execution flow.

# Enterprise AI Application Orchestration Platform

## Data Model & API Specification

**Version:** 1.0  
**Status:** MVP Engineering Specification

---

# 1. Purpose

This document defines the implementation contracts for the MVP:

- PostgreSQL data model
    
- Entity relationships
    
- SQLAlchemy model structure
    
- REST API contracts
    
- OpenAI-compatible API
    
- Provider abstraction
    
- Routing-policy schema
    
- Workflow IR
    
- Execution model
    
- Error model
    
- Authentication model
    

The goal is to remove ambiguity before implementation begins.

---

# 2. System Boundaries

The platform has five major logical boundaries:

```text
┌─────────────────────────────────────────────────────┐
│                  EXPERIENCE LAYER                   │
│                                                     │
│ React / Next.js Dashboard                           │
└───────────────────────┬─────────────────────────────┘
                        │
                        ▼
┌─────────────────────────────────────────────────────┐
│                     API LAYER                       │
│                                                     │
│ FastAPI                                             │
│ Admin API + OpenAI-compatible API                   │
└───────────────────────┬─────────────────────────────┘
                        │
                        ▼
┌─────────────────────────────────────────────────────┐
│                 APPLICATION RUNTIME                 │
│                                                     │
│ Policy → Routing → Workflow → Execution             │
└───────────┬──────────────┬──────────────┬───────────┘
            │              │              │
            ▼              ▼              ▼
       PostgreSQL        Redis       Provider Layer
                                           │
                              ┌────────────┼────────────┐
                              ▼            ▼            ▼
                           OpenAI       Ollama       vLLM
```

---

# 3. Database Design

PostgreSQL is the system of record.

The schema is divided into:

```text
Identity
Application
Provider
Model
Workflow
Prompt
Runtime
Routing
Billing/Cost
Audit
```

---

# 4. Entity Relationship Model

```text
Organization
    │
    └── Workspace
          │
          ├── Users
          │
          ├── Applications
          │       │
          │       ├── API Keys
          │       ├── Policies
          │       ├── Workflows
          │       └── Executions
          │
          └── Provider Connections
                    │
                    └── Models
```

Runtime:

```text
Application
     │
     ▼
Workflow
     │
     ▼
Execution
     │
     ├── Routing Decision
     │
     └── Model Executions
             │
             └── Provider
```

---

# 5. Organization

```text
organizations
```

|Column|Type|Description|
|---|---|---|
|id|UUID|Primary key|
|name|VARCHAR|Organization name|
|slug|VARCHAR|Unique identifier|
|status|VARCHAR|active/suspended|
|created_at|TIMESTAMP|Creation time|
|updated_at|TIMESTAMP|Last update|

Example:

```json
{
  "id": "org_01",
  "name": "Acme AI",
  "slug": "acme-ai",
  "status": "active"
}
```

---

# 6. Workspace

```text
workspaces
```

A workspace isolates applications, models, credentials and users.

```text
organizations
      │
      └── workspaces
```

Columns:

```text
id
organization_id
name
slug
status
created_at
updated_at
```

Constraint:

```text
organization_id + slug = UNIQUE
```

---

# 7. Users

```text
users
```

Columns:

```text
id
email
password_hash
name
status
created_at
updated_at
```

Do not store plaintext passwords.

---

# 8. Workspace Members

```text
workspace_members
```

Columns:

```text
id
workspace_id
user_id
role
created_at
```

Roles:

```text
OWNER
ADMIN
DEVELOPER
VIEWER
```

---

# 9. Applications

This is one of the central entities.

```text
applications
```

Columns:

```text
id
workspace_id
name
slug
description
environment
status
default_workflow_id
created_at
updated_at
```

Environment:

```text
development
staging
production
```

---

# 10. API Keys

```text
api_keys
```

Columns:

```text
id
application_id
name
key_prefix
key_hash
last_used_at
expires_at
status
created_at
```

Important:

```text
Raw API key
      │
      ▼
Hash
      │
      ▼
Database
```

Only the prefix should be retained for identification.

Example:

```text
eaop_sk_8f72...
```

---

# 11. Provider Connections

A provider connection represents a configured provider credential.

```text
providers
```

Columns:

```text
id
workspace_id
name
type
base_url
credential_reference
status
created_at
updated_at
```

Provider types:

```text
openai
ollama
anthropic
gemini
openai_compatible
vllm
```

---

# 12. Models

```text
models
```

Columns:

```text
id
provider_id
model_identifier
display_name
version
context_window
input_price_per_1m
output_price_per_1m
capabilities
status
created_at
updated_at
```

`capabilities` can initially be PostgreSQL JSONB.

Example:

```json
{
  "chat": true,
  "streaming": true,
  "tools": true,
  "vision": false,
  "json_mode": true
}
```

---

# 13. Model Benchmarks

```text
model_benchmarks
```

Columns:

```text
id
model_id
benchmark_suite
prompt_tokens
output_tokens
load_time_ms
ttft_ms
total_latency_ms
tokens_per_second
memory_mb
cpu_percent
gpu_percent
estimated_cost
error_rate
quality_score
created_at
```

This table allows historical comparison.

---

# 14. Prompts

```text
prompts
```

Columns:

```text
id
application_id
name
description
active_version
created_at
updated_at
```

Prompt versions:

```text
prompt_versions
```

Columns:

```text
id
prompt_id
version
template
variables
created_by
created_at
```

Constraint:

```text
prompt_id + version = UNIQUE
```

---

# 15. Workflows

```text
workflows
```

Columns:

```text
id
application_id
name
description
active_version
status
created_at
updated_at
```

Workflow versions:

```text
workflow_versions
```

Columns:

```text
id
workflow_id
version
definition
created_by
created_at
```

`definition` is JSONB.

---

# 16. Routing Policies

```text
routing_policies
```

Columns:

```text
id
application_id
name
strategy
configuration
status
created_at
updated_at
```

Example:

```json
{
  "strategy": "weighted_score",
  "constraints": {
    "max_latency_ms": 3000,
    "max_cost": 0.01,
    "required_capabilities": [
      "chat"
    ]
  },
  "weights": {
    "quality": 0.5,
    "latency": 0.2,
    "cost": 0.3
  }
}
```

---

# 17. Application Policies

```text
application_policies
```

Example policy types:

```text
MODEL_ALLOWLIST
MODEL_DENYLIST
MAX_COST
MAX_TOKENS
MAX_LATENCY
DATA_POLICY
RATE_LIMIT
```

Example:

```json
{
  "type": "MODEL_ALLOWLIST",
  "models": [
    "model_001",
    "model_002"
  ]
}
```

---

# 18. Executions

Every request that enters the platform should have an execution record.

```text
executions
```

Columns:

```text
id
application_id
workflow_id
status
request_id
input_tokens
output_tokens
total_tokens
total_latency_ms
estimated_cost
error_code
created_at
completed_at
```

Status:

```text
PENDING
RUNNING
SUCCESS
FAILED
CANCELLED
```

---

# 19. Model Executions

One execution may involve multiple model attempts.

```text
executions
       │
       ├── model_execution #1
       ├── model_execution #2
       └── model_execution #3
```

Table:

```text
model_executions
```

Columns:

```text
id
execution_id
model_id
provider_id
attempt_number
status
prompt_tokens
output_tokens
ttft_ms
latency_ms
estimated_cost
error_code
started_at
completed_at
```

This enables fallback analysis.

---

# 20. Audit Logs

```text
audit_logs
```

Columns:

```text
id
workspace_id
actor_id
action
resource_type
resource_id
metadata
created_at
```

Examples:

```text
MODEL_CREATED
MODEL_UPDATED
PROVIDER_ADDED
API_KEY_CREATED
POLICY_CHANGED
WORKFLOW_PUBLISHED
```

---

# 21. Database Relationship Summary

```text
Organization
    │
    └── Workspace
          │
          ├── Users
          ├── Applications
          │      │
          │      ├── API Keys
          │      ├── Prompts
          │      ├── Workflows
          │      ├── Routing Policies
          │      └── Executions
          │             │
          │             └── Model Executions
          │
          └── Providers
                 │
                 └── Models
                        │
                        └── Benchmarks
```

---

# 22. SQLAlchemy Structure

Recommended organization:

```text
apps/api/
└── models/
    ├── organization.py
    ├── workspace.py
    ├── user.py
    ├── application.py
    ├── provider.py
    ├── model.py
    ├── workflow.py
    ├── prompt.py
    ├── execution.py
    └── audit.py
```

Example:

```python
class Application(Base):
    __tablename__ = "applications"

    id = Column(UUID, primary_key=True)
    workspace_id = Column(
        UUID,
        ForeignKey("workspaces.id"),
        nullable=False
    )

    name = Column(String, nullable=False)
    slug = Column(String, nullable=False)
    environment = Column(String, nullable=False)
    status = Column(String, nullable=False)

    created_at = Column(DateTime, nullable=False)
    updated_at = Column(DateTime, nullable=False)
```

---

# 23. API Architecture

Separate APIs into two categories.

## Management API

```text
/api/v1/...
```

Used by:

- Dashboard
    
- CLI
    
- Platform administrators
    
- Developers
    

## Runtime API

```text
/v1/...
```

Used by:

- AI applications
    
- SDKs
    
- external systems
    

This distinction is important.

---

# 24. Authentication

Management API:

```text
Authorization: Bearer <JWT>
```

Runtime API:

```text
Authorization: Bearer eaop_sk_xxxxx
```

The runtime key resolves directly to an application.

---

# 25. Application API

### Create

```http
POST /api/v1/applications
```

Request:

```json
{
  "name": "Customer Support AI",
  "description": "AI support application",
  "environment": "development"
}
```

Response:

```json
{
  "id": "app_123",
  "name": "Customer Support AI",
  "environment": "development",
  "status": "active"
}
```

---

# 26. Provider API

### Register provider

```http
POST /api/v1/providers
```

Request:

```json
{
  "name": "Local Ollama",
  "type": "ollama",
  "base_url": "http://ollama:11434"
}
```

For cloud providers:

```json
{
  "name": "OpenAI Production",
  "type": "openai",
  "credential": "..."
}
```

The actual credential should not be returned in API responses.

---

# 27. Model API

```http
POST /api/v1/models
```

Request:

```json
{
  "provider_id": "provider_123",
  "model_identifier": "llama3.1:8b",
  "display_name": "Llama 3.1 8B",
  "context_window": 128000,
  "capabilities": {
    "chat": true,
    "streaming": true,
    "tools": true
  }
}
```

---

# 28. Model Discovery API

```http
GET /v1/models
```

Response:

```json
{
  "object": "list",
  "data": [
    {
      "id": "model_001",
      "object": "model",
      "owned_by": "eaop"
    },
    {
      "id": "model_002",
      "object": "model",
      "owned_by": "eaop"
    }
  ]
}
```

---

# 29. OpenAI-Compatible Chat API

```http
POST /v1/chat/completions
```

Request:

```json
{
  "model": "auto",
  "messages": [
    {
      "role": "system",
      "content": "You are a helpful assistant."
    },
    {
      "role": "user",
      "content": "Explain containers."
    }
  ],
  "temperature": 0.2,
  "max_tokens": 500,
  "stream": false
}
```

---

# 30. Explicit Model Selection

The developer may choose:

```json
{
  "model": "model_001"
}
```

In this mode:

```text
Provider selection
        ↓
Direct model execution
```

Routing is bypassed except for mandatory policies.

---

# 31. Automatic Model Selection

Developer chooses:

```json
{
  "model": "auto"
}
```

Then:

```text
Request
   ↓
Policy
   ↓
Router
   ↓
Candidate Models
   ↓
Scoring
   ↓
Selected Model
```

This is the central platform feature.

---

# 32. OpenAI-Compatible Response

Example:

```json
{
  "id": "chatcmpl_eaop_123",
  "object": "chat.completion",
  "created": 1790000000,
  "model": "model_001",
  "choices": [
    {
      "index": 0,
      "message": {
        "role": "assistant",
        "content": "Containers package applications..."
      },
      "finish_reason": "stop"
    }
  ],
  "usage": {
    "prompt_tokens": 42,
    "completion_tokens": 71,
    "total_tokens": 113
  }
}
```

The API should remain compatible with common OpenAI SDK clients.

---

# 33. Streaming

For:

```json
{
  "stream": true
}
```

the gateway should return Server-Sent Events.

Conceptually:

```text
data: {"choices":[{"delta":{"content":"Containers"}}]}

data: {"choices":[{"delta":{"content":" package"}}]}

data: {"choices":[{"delta":{"content":" applications"}}]}

data: [DONE]
```

The provider adapter handles provider-specific streaming formats and converts them into the normalized stream.

---

# 34. Provider Interface

The most important internal interface:

```python
class ProviderAdapter(Protocol):

    async def chat(
        self,
        request: ChatRequest
    ) -> ChatResponse:
        ...

    async def stream(
        self,
        request: ChatRequest
    ) -> AsyncIterator[ChatChunk]:
        ...

    async def health_check(self) -> HealthStatus:
        ...

    async def list_models(self) -> list[ModelInfo]:
        ...
```

The router should never know how a provider works internally.

---

# 35. Normalized Request

Internally:

```python
@dataclass
class ChatRequest:

    model: str
    messages: list[Message]

    temperature: float | None = None
    max_tokens: int | None = None

    tools: list[ToolDefinition] | None = None

    stream: bool = False
```

---

# 36. Normalized Response

```python
@dataclass
class ChatResponse:

    content: str

    model: str

    finish_reason: str

    usage: Usage

    latency_ms: float

    ttft_ms: float | None

    provider_request_id: str | None
```

---

# 37. Routing Request

The router should receive a normalized request rather than an HTTP request.

```python
@dataclass
class RoutingRequest:

    application_id: str

    requested_model: str

    messages: list[Message]

    required_capabilities: set[str]

    max_cost: float | None

    max_latency_ms: int | None

    stream: bool
```

---

# 38. Routing Result

```python
@dataclass
class RoutingDecision:

    selected_model_id: str

    provider_id: str

    strategy: str

    score: float

    candidates: list[Candidate]

    excluded: list[ExcludedCandidate]
```

This object should be persisted with the execution.

---

# 39. Routing Algorithm

MVP algorithm:

```python
def route(request):

    candidates = discover_models(request)

    candidates = filter_capabilities(
        candidates,
        request.required_capabilities
    )

    candidates = filter_policy(
        candidates,
        request.application_id
    )

    candidates = filter_health(
        candidates
    )

    candidates = filter_constraints(
        candidates,
        request
    )

    return score_and_select(candidates)
```

---

# 40. Candidate Scoring

Each model receives:

```text
quality_score
latency_score
cost_score
availability_score
```

Then:

```text
Final Score =
    Wq × Quality
  + Wl × Latency
  + Wc × Cost
  + Wa × Availability
```

Weights come from the routing policy.

---

# 41. Workflow Intermediate Representation

The workflow definition should be independent of the frontend.

Example:

```json
{
  "version": "1.0",
  "entrypoint": "input",

  "nodes": [
    {
      "id": "input",
      "type": "input"
    },
    {
      "id": "llm_1",
      "type": "llm",
      "config": {
        "model": "auto",
        "prompt": "support-classifier"
      }
    },
    {
      "id": "output",
      "type": "output"
    }
  ],

  "edges": [
    {
      "source": "input",
      "target": "llm_1"
    },
    {
      "source": "llm_1",
      "target": "output"
    }
  ]
}
```

---

# 42. Workflow Execution

```text
Workflow Definition
        │
        ▼
Validate Graph
        │
        ▼
Initialize State
        │
        ▼
Find Entry Node
        │
        ▼
Execute Node
        │
        ▼
Update State
        │
        ▼
Resolve Next Node
        │
        ▼
Execute Next Node
        │
       ...
        │
        ▼
Output
```

---

# 43. Conditional Node

Example:

```json
{
  "id": "condition_1",
  "type": "condition",

  "config": {
    "expression": "state.classification == 'technical'"
  }
}
```

Edges:

```text
condition
   │
   ├── true  → technical_response
   │
   └── false → general_response
```

---

# 44. Workflow State Contract

```json
{
  "input": {},
  "variables": {},
  "node_outputs": {},
  "metadata": {},
  "usage": {},
  "errors": []
}
```

Example:

```json
{
  "input": {
    "question": "How do I reset my password?"
  },

  "node_outputs": {
    "classifier": {
      "category": "account"
    }
  },

  "usage": {
    "total_tokens": 421
  }
}
```

---

# 45. Execution Pipeline

The actual runtime should follow this sequence:

```text
┌───────────────────────────┐
│ HTTP Request              │
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ Authenticate              │
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ Resolve Application       │
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ Validate Request          │
└─────────────┬─────────────┘
              ▼
┌───────────────────────────┐
│ Policy Evaluation         │
└─────────────┬─────────────┘
              ▼
       model == "auto"?
          /         \
        yes          no
         │            │
         ▼            │
┌────────────────┐    │
│ Routing Engine │    │
└───────┬────────┘    │
        │             │
        └──────┬──────┘
               ▼
       ┌───────────────┐
       │ Model Adapter │
       └───────┬───────┘
               ▼
             LLM
               │
               ▼
       Normalize Response
               │
        ┌──────┴──────┐
        ▼             ▼
     Metrics        Trace
        │             │
        └──────┬──────┘
               ▼
            Response
```

---

# 46. Retry and Fallback Execution

Pseudo-code:

```python
for candidate in candidates:

    try:
        response = await execute(candidate)

        return response

    except RetryableError as error:

        record_failure(candidate, error)

        if can_retry(candidate):
            await backoff()
            continue

        if has_fallback():
            continue

        raise

    except NonRetryableError:
        raise
```

The distinction between retry and fallback should be explicit.

---

# 47. Error Contract

All API errors should use a normalized format.

```json
{
  "error": {
    "message": "The selected model is unavailable.",
    "type": "provider_unavailable",
    "code": "MODEL_UNAVAILABLE",
    "request_id": "req_123"
  }
}
```

Possible codes:

```text
AUTHENTICATION_ERROR
AUTHORIZATION_ERROR
INVALID_REQUEST
MODEL_NOT_FOUND
MODEL_UNAVAILABLE
PROVIDER_TIMEOUT
PROVIDER_RATE_LIMIT
PROVIDER_ERROR
POLICY_DENIED
BUDGET_EXCEEDED
CONTEXT_LENGTH_EXCEEDED
ROUTING_FAILED
WORKFLOW_FAILED
INTERNAL_ERROR
```

---

# 48. Request Correlation

Every request should receive:

```text
request_id
execution_id
trace_id
```

Example:

```text
Request ID:
req_01H...

Execution ID:
exec_01H...

Trace ID:
4bf92f3577...
```

These IDs must appear in logs and API responses where appropriate.

---

# 49. Cost Calculation Pipeline

```text
Provider Response
       │
       ▼
Extract Usage
       │
       ▼
Resolve Model Pricing
       │
       ▼
Calculate Cost
       │
       ▼
Store Model Execution
       │
       ▼
Aggregate Application Cost
```

---

# 50. Benchmark Contract

Benchmark request:

```json
{
  "name": "general-chat-v1",
  "models": [
    "model_001",
    "model_002"
  ],
  "iterations": 10,
  "dataset": "basic-chat"
}
```

Benchmark result:

```json
{
  "model": "model_001",
  "iterations": 10,
  "avg_latency_ms": 1320,
  "p95_latency_ms": 1820,
  "ttft_ms": 390,
  "tokens_per_second": 48.2,
  "error_rate": 0.0,
  "estimated_cost": 0.031
}
```

---

# 51. Background Job Architecture

Long-running operations should not block the API.

Examples:

```text
Benchmark
Model health checks
Large workflow execution
Evaluation
Embedding jobs
Dataset processing
```

Flow:

```text
API
 │
 ├── Create Job
 │
 ▼
Redis Queue
 │
 ▼
Worker
 │
 ▼
Execute
 │
 ▼
Store Result
```

---

# 52. Redis Keys

Use namespaced keys.

```text
eaop:rate:{application_id}
eaop:health:{provider_id}
eaop:model_health:{model_id}
eaop:job:{job_id}
eaop:lock:{resource}
eaop:cache:{key}
```

Use TTLs wherever appropriate.

---

# 53. Idempotency

For operations that may have side effects:

```http
Idempotency-Key: 8e3f...
```

Example:

```http
POST /api/v1/benchmarks
Idempotency-Key: benchmark-123
```

If the same request is submitted twice, the server should not create duplicate jobs.

---

# 54. Versioning

Every mutable production artifact should be versioned.

```text
Prompt
Workflow
Routing Policy
Model Pricing
Benchmark Suite
```

Example:

```text
workflow:v3
prompt:v8
routing-policy:v2
```

Production executions should record the versions used.

---

# 55. Configuration Precedence

Configuration should have deterministic precedence.

Recommended:

```text
Request
   ↓
Application
   ↓
Workflow
   ↓
Routing Policy
   ↓
Workspace
   ↓
Platform Defaults
```

More specific configuration overrides less specific configuration, subject to security policies.

---

# 56. Example End-to-End Request

Developer:

```python
client.chat.completions.create(
    model="auto",
    messages=[
        {
            "role": "user",
            "content": "Summarize this document."
        }
    ]
)
```

EAOP internally:

```text
1. Authenticate API key

2. Resolve application

3. Load application policy

4. Identify requirements

5. Discover candidate models

6. Remove unsupported models

7. Remove policy-denied models

8. Remove unhealthy models

9. Apply cost constraint

10. Apply latency constraint

11. Score candidates

12. Select model

13. Execute provider adapter

14. Retry if appropriate

15. Fallback if required

16. Normalize response

17. Calculate tokens

18. Calculate cost

19. Record execution

20. Emit telemetry

21. Return response
```

---

# 57. MVP Repository Mapping

The database and API contracts map to the repository as follows:

```text
apps/api/
│
├── routes/
│   ├── applications.py
│   ├── providers.py
│   ├── models.py
│   ├── workflows.py
│   ├── prompts.py
│   ├── executions.py
│   └── runtime.py
│
├── models/
│   ├── application.py
│   ├── provider.py
│   ├── model.py
│   ├── workflow.py
│   ├── prompt.py
│   └── execution.py
│
├── services/
│   ├── application_service.py
│   ├── provider_service.py
│   ├── model_service.py
│   ├── workflow_service.py
│   └── execution_service.py
│
└── core/
    ├── auth.py
    ├── config.py
    └── database.py
```

Packages:

```text
packages/
│
├── providers/
│   ├── base.py
│   ├── openai.py
│   ├── ollama.py
│   └── generic.py
│
├── routing-engine/
│   ├── router.py
│   ├── filters.py
│   ├── scoring.py
│   └── policies.py
│
├── workflow-ir/
│   ├── schema.py
│   ├── validator.py
│   └── executor.py
│
└── telemetry/
    ├── tracing.py
    ├── metrics.py
    └── logging.py
```

---

# 58. What Should Be Built First

Do not begin with the dashboard.

The implementation sequence should be:

```text
                    START
                      │
                      ▼
              PostgreSQL Schema
                      │
                      ▼
               FastAPI Skeleton
                      │
                      ▼
             Provider Interface
                      │
                      ▼
               Ollama Adapter
                      │
                      ▼
            OpenAI-Compatible API
                      │
                      ▼
               Model Registry
                      │
                      ▼
               Basic Router
                      │
                      ▼
             Execution Tracking
                      │
                      ▼
              Retry / Fallback
                      │
                      ▼
               Cost Tracking
                      │
                      ▼
              Workflow Runtime
                      │
                      ▼
                Observability
                      │
                      ▼
                 Dashboard
```

---

# 59. First Vertical Slice

The first coding milestone should be deliberately small.

### Build only:

```text
FastAPI
PostgreSQL
Ollama
Provider interface
Model registry
/v1/chat/completions
Simple router
Execution table
```

Then verify:

```bash
curl http://localhost:8000/v1/chat/completions \
  -H "Authorization: Bearer eaop_sk_test" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "auto",
    "messages": [
      {
        "role": "user",
        "content": "What is Docker?"
      }
    ]
  }'
```

Expected behavior:

```text
curl
 │
 ▼
EAOP
 │
 ▼
Router
 │
 ▼
Ollama
 │
 ▼
Response
```

Once this works, add a second provider.

Then:

```text
Provider A
Provider B
     │
     ▼
  Router
     │
     ▼
 Selected Provider
```

That becomes the first true demonstration of EAOP.

---

# 60. Architectural Acceptance Test

The most important architectural test is:

> **Can the application switch between providers without changing application code?**

For example:

```text
Before:

model = "openai-model"
```

and later:

```text
model = "auto"
```

while EAOP decides:

```text
Request #1 → Provider A
Request #2 → Provider B
Request #3 → Provider A
Request #4 → Provider C
```

based on configured constraints.

If this works while maintaining traceability, cost tracking, retries, and policy enforcement, the core platform architecture is validated.

---

# 61. Next Engineering Artifact

After this specification, the project is ready for the **actual implementation blueprint**:

```text
1. PostgreSQL migration
2. SQLAlchemy models
3. Pydantic schemas
4. FastAPI project structure
5. Provider interface
6. Ollama adapter
7. OpenAI adapter
8. Model registry service
9. Router implementation
10. Retry/fallback middleware
11. Execution service
12. Docker Compose
13. Seed data
14. Test suite
15. First curl request
```

That should be the next step before building advanced workflow or UI functionality.