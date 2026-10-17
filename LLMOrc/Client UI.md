# EAOP Client UI — Frontend Team Specification

This should be treated as the **frontend handoff specification for the EAOP Client MVP**.

The key principle is:

> **The Client is not just a chatbot UI. It is a visual interface to the EAOP orchestration runtime.**

The frontend must make three things obvious:

1. **What the user asked**
    
2. **What EAOP decided to do**
    
3. **What happened during execution**
    

---

# 1. Client Scope

The EAOP Client MVP has **one primary workflow**:

```text
Connect Providers
       ↓
Discover Models
       ↓
Open Playground
       ↓
Enter Prompt
       ↓
AUTO Mode
       ↓
EAOP Runtime
       ↓
Response
       ↓
Execution Details
```

The frontend should **not** expose the entire platform architecture to the user.

The user experience should remain simple:

```text
┌─────────────────────────────────────────────┐
│                 EAOP Client                 │
│                                             │
│  Ask anything...                            │
│                                             │
│  [ Prompt ................................] │
│                              [ Send → ]     │
└─────────────────────────────────────────────┘
```

The complexity appears progressively when the user wants to inspect it.

---

# 2. Application Shell

Desktop-first layout:

```text
┌──────────────────────────────────────────────────────────────────────┐
│ EAOP                                             ● Runtime Healthy   │
├──────────────┬──────────────────────────────────────┬───────────────┤
│              │                                      │               │
│ SIDEBAR      │             PLAYGROUND               │ EXECUTION     │
│              │                                      │ PANEL         │
│ + New Chat   │                                      │               │
│              │                                      │               │
│ Conversations│                                      │               │
│              │                                      │               │
│ Today        │          Conversation                │               │
│  Explain API │                                      │               │
│  Debug Java  │                                      │               │
│  SQL Query   │                                      │               │
│              │                                      │               │
│ Yesterday    │                                      │               │
│  Kubernetes  │                                      │               │
│              │                                      │               │
│              │                                      │               │
│              │                                      │               │
│              │                                      │               │
│ Settings     │                                      │               │
└──────────────┴──────────────────────────────────────┴───────────────┘
```

### Width recommendations

```text
Sidebar:          240–280px
Main content:     flexible
Execution panel:  320–380px
```

The execution panel should be **collapsible**.

---

# 3. Navigation

Keep the Client navigation intentionally small.

```text
EAOP
│
├── New Chat
│
├── Conversations
│
├── Providers
│
└── Settings
```

Do **not** put these into the Client sidebar:

- Models
    
- Routing Policies
    
- Benchmarks
    
- Workflows
    
- RAG
    
- Agents
    
- Audit
    
- Analytics
    

Those belong in the **EAOP Console**.

The Client is the execution experience.

---

# 4. Sidebar

### Header

```text
┌────────────────────────┐
│ ◈ EAOP                 │
│ Enterprise AI Runtime  │
└────────────────────────┘
```

### New Chat

```text
┌────────────────────────┐
│ ＋ New Chat             │
└────────────────────────┘
```

### Conversation list

Group by date:

```text
TODAY

Explain Kubernetes
Java LRU Cache
SQL optimization

YESTERDAY

REST vs SOAP
Docker explanation
```

Each conversation item:

```text
Explain Kubernetes
Today · 11:32 AM
```

Maximum title length:

```text
~32 characters
```

Overflow:

```text
Explain Kubernetes and...
```

---

# 5. Main Playground

This is the **most important screen in the entire Client**.

The default state:

```text
                    EAOP

              AI Playground

       Ask EAOP to build, explain,
       analyze or solve something.

        ┌─────────────────────────┐
        │                         │
        │                         │
        │                         │
        │                         │
        └─────────────────────────┘

 ┌─────────────────────────────────────────────┐
 │ Ask EAOP anything...                    ↑  │
 └─────────────────────────────────────────────┘

             AUTO · Balanced · 14 models
```

Don't overcrowd this screen.

---

# 6. Prompt Composer

The composer is the primary interaction.

```text
┌──────────────────────────────────────────────────┐
│                                                  │
│ Ask EAOP anything...                             │
│                                                  │
│                                                  │
│                                                  │
├──────────────────────────────────────────────────┤
│ ＋  Attach       AUTO ▼       Balanced ▼     ↑   │
└──────────────────────────────────────────────────┘
```

### MVP controls

**Left**

```text
＋
```

Optional attachment support can initially be disabled.

**Center**

```text
AUTO ▼
```

**Routing strategy**

```text
Balanced ▼
```

**Right**

```text
↑ Send
```

---

# 7. Execution Mode Selector

Clicking `AUTO` opens:

```text
┌────────────────────────────────┐
│ Execution Mode                 │
├────────────────────────────────┤
│ ● AUTO                         │
│   EAOP selects the model       │
│   and execution strategy.      │
│                                │
│ ○ DIRECT                       │
│   Use a specific model.        │
│                                │
│ ─────────────────────────────  │
│ WORKFLOW                 Soon  │
│ RAG                      Soon  │
│ AGENT                    Soon  │
└────────────────────────────────┘
```

For MVP:

- AUTO = enabled
    
- DIRECT = optional
    
- WORKFLOW/RAG/AGENT = disabled with `Coming Soon`
    

---

# 8. Routing Strategy Selector

MVP:

```text
Balanced
```

Dropdown:

```text
┌──────────────────────────────┐
│ Routing Strategy             │
├──────────────────────────────┤
│ ● Balanced                   │
│   Quality + latency + cost   │
│                              │
│ ○ Quality                    │
│   Prefer higher capability   │
│                              │
│ ○ Speed                      │
│   Prefer lower latency       │
│                              │
│ ○ Cost                       │
│   Prefer lower cost          │
└──────────────────────────────┘
```

These settings should be sent to the backend.

Example:

```json
{
  "mode": "auto",
  "strategy": "balanced"
}
```

---

# 9. Empty State

The empty playground should provide useful examples.

```text
What would you like to do?

┌────────────────────┐
│ Explain a concept  │
│ "Explain Docker..."│
└────────────────────┘

┌────────────────────┐
│ Write code         │
│ "Build a Java..."  │
└────────────────────┘

┌────────────────────┐
│ Analyze something  │
│ "Analyze this..."  │
└────────────────────┘
```

Clicking a suggestion should populate the composer, **not automatically submit**.

---

# 10. User Message

Once submitted:

```text
┌──────────────────────────────────────────────┐
│ YOU                                          │
│                                              │
│ Explain Kubernetes to me like I'm preparing │
│ for an MCA lab exam.                         │
└──────────────────────────────────────────────┘
```

Keep user messages visually lighter than assistant output.

---

# 11. AI Response

```text
┌──────────────────────────────────────────────┐
│ EAOP                                         │
│                                              │
│ Kubernetes is an open-source container       │
│ orchestration platform...                    │
│                                              │
│ ...                                          │
│                                              │
│ ───────────────────────────────────────────  │
│ llama3.1:8b · 1.42s · 482 tokens             │
│                                              │
│ [ View Execution ]                           │
└──────────────────────────────────────────────┘
```

The metadata line is important.

It immediately communicates:

```text
Model
Latency
Tokens
```

---

# 12. Execution Status

When the request is executing, don't show only:

> Thinking...

Instead expose the orchestration process.

```text
EAOP is routing your request...

✓ Request received
✓ Intent analyzed
✓ Task classified
✓ Candidate models evaluated
✓ Model selected

● Generating response...
```

This can be displayed beneath the user prompt or inside the execution panel.

---

# 13. Execution Panel

The right panel is the **signature feature** of the Client.

Default state after execution:

```text
┌──────────────────────────────────┐
│ EXECUTION                        │
│                                  │
│ ● Success                        │
│                                  │
│ Technical Explanation            │
│ AUTO                             │
│                                  │
│ ───────────────────────────────  │
│ MODEL                            │
│                                  │
│ llama3.1:8b                      │
│ Ollama                           │
│                                  │
│ ───────────────────────────────  │
│ PERFORMANCE                      │
│                                  │
│ TTFT              280 ms         │
│ Total latency     1.42 s         │
│ Tokens/sec        71             │
│                                  │
│ ───────────────────────────────  │
│ USAGE                            │
│                                  │
│ Input             148            │
│ Output            334            │
│ Total             482            │
│                                  │
│ Estimated cost    $0.0000        │
│                                  │
│ [ View Execution Path ]          │
│ [ Why this model? ]              │
└──────────────────────────────────┘
```

---

# 14. Execution Path

Clicking **View Execution Path** opens an expanded trace.

```text
EXECUTION PATH

● Request
│
▼
● Gateway
│
▼
● Input Guardrails
│
▼
● Intent Analyzer
│
│  Technical Explanation
│
▼
● Task Classifier
│
│  Medium Complexity
│
▼
● Model Router
│
│  6 candidates
│
▼
● Llama 3.1 8B
│
│  Ollama
│
▼
● Output Guardrails
│
▼
● Response
```

Each node should be clickable.

---

# 15. Node Detail

Clicking:

```text
Intent Analyzer
```

opens:

```text
┌─────────────────────────────┐
│ Intent Analyzer             │
├─────────────────────────────┤
│ Task                         │
│ Technical Explanation       │
│                             │
│ Domain                       │
│ Software / Cloud             │
│                             │
│ Complexity                   │
│ Medium                       │
│                             │
│ Confidence                   │
│ 0.91                         │
└─────────────────────────────┘
```

This gives the user visibility into EAOP's decisions.

---

# 16. “Why This Model?”

This needs its own component.

```text
Why was this model selected?

Selected model

┌──────────────────────────────┐
│ Llama 3.1 8B                 │
│ Ollama                       │
└──────────────────────────────┘

Selection factors

Capability       90%
Latency         100%
Cost            100%
Availability     95%

Strategy
Balanced

Candidates evaluated
6

Decision

Selected because it met the task capability
requirements while providing favorable
latency and cost characteristics.
```

Avoid making the UI claim that a model is mathematically “best” unless the backend actually provides that conclusion.

Use:

> **Selected according to the configured routing strategy.**

---

# 17. Candidate Models

Expandable section:

```text
Candidate Models

1  Llama 3.1 8B        Selected
2  Qwen 2.5 7B
3  Gemini Flash
4  GPT-4.1 Mini
5  Mistral 7B
6  Claude Haiku
```

Expanded:

```text
┌────────────────────────────────────────────┐
│ Llama 3.1 8B                         ✓     │
│                                            │
│ Capability      0.90                       │
│ Latency         0.96                       │
│ Cost            1.00                       │
│ Availability    0.95                       │
│                                            │
│ Final score     0.94                       │
└────────────────────────────────────────────┘
```

---

# 18. Metrics Cards

The UI should standardize metrics.

### Latency

```text
1.42s
Total Latency
```

### TTFT

```text
280ms
Time to First Token
```

### Throughput

```text
71
Tokens / sec
```

### Usage

```text
482
Total Tokens
```

### Cost

```text
$0.0000
Estimated Cost
```

Use the backend-provided values rather than calculating them independently in the frontend.

---

# 19. Streaming UI

For `stream=true`:

```text
Generating...

Kubernetes is an open-source
container orchestration platform...
▌
```

The cursor should appear while streaming.

At completion:

```text
✓ Complete
```

The execution metrics should update after the stream finishes.

---

# 20. Error State

Do **not** show raw provider errors.

Bad:

```text
ConnectionError: HTTP 503 ...
```

Instead:

```text
┌──────────────────────────────────────────┐
│ Unable to complete request               │
│                                          │
│ The selected model is currently         │
│ unavailable.                             │
│                                          │
│ EAOP attempted a fallback model.         │
│                                          │
│ [ Retry ]       [ View Execution ]       │
└──────────────────────────────────────────┘
```

If fallback succeeds:

```text
⚠ Fallback used

Primary:
Llama 3.1 8B

Fallback:
Qwen 2.5 7B

Reason:
Primary provider unavailable.
```

---

# 21. Provider Screen

The Client needs a lightweight provider management page.

```text
Providers

┌───────────────────────────────────────────┐
│ Ollama                         ● Connected │
│ localhost:11434                           │
│ 12 models                                 │
│                                           │
│ [ Manage ]                                │
└───────────────────────────────────────────┘

┌───────────────────────────────────────────┐
│ OpenAI                         ● Connected │
│ 8 models                                  │
│                                           │
│ [ Manage ]                                │
└───────────────────────────────────────────┘

             + Add Provider
```

---

# 22. Add Provider

```text
Add Provider

Provider

[ Ollama ▼ ]

Connection

Base URL
[ http://localhost:11434 ]

API Key
[ ••••••••••••• ]

[ Test Connection ]

────────────────────────

Models discovered

✓ llama3.1:8b
✓ qwen2.5:7b
✓ mistral:7b

[ Save Provider ]
```

---

# 23. Settings

Keep Client settings minimal.

```text
Settings

Account
├── Profile
└── Workspace

Runtime
├── Default Mode
├── Default Routing Strategy
└── Streaming

Providers
└── Manage Connections

Appearance
├── Theme
└── Density
```

---

# 24. Responsive Behavior

### Desktop

Three-column:

```text
Sidebar | Chat | Execution
```

### Tablet

Two-column:

```text
Sidebar | Chat
             ↘ Execution Drawer
```

### Mobile

Single-column:

```text
Chat

Execution
  ↓
Bottom Sheet
```

The execution panel should become a bottom sheet.

---

# 25. Frontend State Model

The frontend should maintain a normalized execution state.

```typescript
interface Execution {
  id: string;

  status:
    | "queued"
    | "analyzing"
    | "routing"
    | "executing"
    | "completed"
    | "failed";

  request: {
    prompt: string;
    mode: "auto" | "direct";
    strategy: string;
  };

  intent?: {
    task: string;
    complexity: string;
  };

  routing?: {
    selectedModel: string;
    provider: string;
    strategy: string;
    candidates: CandidateModel[];
  };

  performance?: {
    ttftMs: number;
    latencyMs: number;
    tokensPerSecond: number;
  };

  usage?: {
    inputTokens: number;
    outputTokens: number;
    totalTokens: number;
  };

  cost?: {
    estimated: number;
    currency: string;
  };

  reliability?: {
    retries: number;
    fallbacks: number;
  };

  executionPath: ExecutionStep[];

  response?: string;
}
```

---

# 26. Execution Step

```typescript
interface ExecutionStep {
  id: string;

  type:
    | "gateway"
    | "guardrail"
    | "intent"
    | "classifier"
    | "router"
    | "model"
    | "tool"
    | "retrieval"
    | "output";

  name: string;

  status:
    | "pending"
    | "running"
    | "completed"
    | "failed"
    | "skipped";

  startedAt?: string;
  completedAt?: string;

  durationMs?: number;

  metadata?: Record<string, unknown>;
}
```

This should drive the execution visualization rather than hard-coding UI nodes.

---

# 27. API Contract for Frontend

The frontend team should consume APIs like:

```text
POST   /v1/chat/completions
GET    /v1/models
GET    /api/v1/providers
POST   /api/v1/providers
POST   /api/v1/providers/{id}/test
GET    /api/v1/executions/{id}
GET    /api/v1/executions/{id}/trace
GET    /api/v1/conversations
POST   /api/v1/conversations
```

For streaming:

```text
POST /v1/chat/completions
Content-Type: application/json
Accept: text/event-stream
```

---

# 28. Recommended Frontend Architecture

```text
apps/web/

src/
├── app/
│
├── components/
│   ├── layout/
│   │   ├── AppShell
│   │   ├── Sidebar
│   │   └── Header
│   │
│   ├── chat/
│   │   ├── ChatView
│   │   ├── MessageList
│   │   ├── UserMessage
│   │   ├── AssistantMessage
│   │   └── PromptComposer
│   │
│   ├── execution/
│   │   ├── ExecutionPanel
│   │   ├── ExecutionStatus
│   │   ├── ExecutionMetrics
│   │   ├── ExecutionPath
│   │   ├── ExecutionNode
│   │   ├── ModelSelection
│   │   └── CandidateModels
│   │
│   └── providers/
│       ├── ProviderList
│       ├── ProviderCard
│       └── ProviderForm
│
├── features/
│   ├── chat/
│   ├── executions/
│   ├── providers/
│   └── settings/
│
├── hooks/
│   ├── useChat
│   ├── useStreaming
│   ├── useExecution
│   └── useProviders
│
├── services/
│   ├── api.ts
│   ├── chat.ts
│   ├── executions.ts
│   └── providers.ts
│
├── stores/
│   ├── chatStore
│   ├── executionStore
│   └── settingsStore
│
└── types/
    ├── chat.ts
    ├── execution.ts
    ├── provider.ts
    └── model.ts
```

---

# 29. Component Hierarchy

The main page should roughly become:

```text
AppShell
│
├── Sidebar
│   ├── NewChatButton
│   └── ConversationList
│
├── MainContent
│   │
│   └── ChatView
│       ├── EmptyState
│       ├── MessageList
│       │   ├── UserMessage
│       │   └── AssistantMessage
│       │
│       └── PromptComposer
│           ├── ModeSelector
│           ├── StrategySelector
│           └── SendButton
│
└── ExecutionPanel
    ├── ExecutionHeader
    ├── Status
    ├── ModelInfo
    ├── PerformanceMetrics
    ├── UsageMetrics
    ├── ReliabilityMetrics
    ├── ExecutionPathButton
    └── WhyModelButton
```

---

# 30. Frontend Design Principles

### 1. Progressive disclosure

Don't show everything immediately.

```text
Response
   ↓
Basic metrics
   ↓
Execution details
   ↓
Execution path
   ↓
Node details
   ↓
Candidate models
```

### 2. Runtime-first

Every major UI component should answer:

> **What did EAOP do?**

### 3. Don't fake intelligence

If the backend doesn't provide:

```text
confidence
score
reason
```

the frontend shouldn't invent it.

### 4. Backend owns execution state

Frontend displays:

```text
routing
latency
tokens
cost
trace
```

It should not independently reproduce routing logic.

### 5. Streaming-first

Design the UI around asynchronous execution from day one.

### 6. OpenAI-compatible

The Client should communicate with the same runtime API that external developers can eventually consume.

---

# 31. MVP Acceptance Criteria

The frontend MVP is complete when a user can:

-  Open EAOP Client
    
-  Create a conversation
    
-  Connect a provider
    
-  Discover models
    
-  See connected providers
    
-  Enter a prompt
    
-  Select AUTO mode
    
-  Select routing strategy
    
-  Submit using Enter
    
-  See streaming response
    
-  See selected model
    
-  See provider
    
-  See latency
    
-  See TTFT
    
-  See token usage
    
-  See estimated cost
    
-  See retries/fallbacks
    
-  Open execution details
    
-  View execution path
    
-  View routing explanation
    
-  View candidate models
    
-  Handle provider/model failure gracefully
    
-  Retry failed execution
    
-  Continue conversation
    
-  Switch conversations
    

---

# 32. What Frontend Should NOT Build Yet

Don't spend time on:

```text
❌ Agent Builder
❌ Workflow Canvas
❌ RAG Studio
❌ Multi-agent UI
❌ Complex analytics
❌ Prompt marketplace
❌ Evaluation Studio
❌ Advanced visual workflow editor
❌ Complex model benchmarking UI
❌ Autonomous planning UI
```

Those belong to later phases.

The frontend team's immediate target is:

```text
                 ┌───────────────┐
                 │   EAOP CLIENT │
                 └───────┬───────┘
                         │
                  User enters prompt
                         │
                         ▼
                      AUTO
                         │
                         ▼
                 EAOP Runtime
                         │
            ┌────────────┼────────────┐
            ▼            ▼            ▼
         Analyze       Route       Execute
            │            │            │
            └────────────┼────────────┘
                         ▼
                      Response
                         │
              ┌──────────┴──────────┐
              ▼                     ▼
          Response              Execution
                                  Trace
```

## The frontend team's north star

**The user should feel like they are talking to one AI system, while being able to see that EAOP intelligently orchestrated multiple underlying AI capabilities.**

That gives us a very clear division:

```text
CLIENT
  ↓
Simple experience

RUNTIME
  ↓
Complex intelligence

CONSOLE
  ↓
Complex configuration
```

That should be the **baseline UI contract between the frontend and backend teams**.