<p align="center">
  <img src="logo.png" alt="SYNAR logo" width="180" />
</p>

# SYNAR

**AI control and routing layer where models remain interchangeable and the system stays in control.**

**Website:** https://synar.dev  
**Contact:** kucherenko1988artur1988@gmail.com

---

## What SYNAR is

SYNAR is not designed as a single-model chatbot.

It is a control layer built above language models to manage:

- routing
- policy
- session identity
- prompt assembly
- streaming
- continuation behavior
- runtime control
- future memory and learning layers

Core principle:

> **The model generates. SYNAR decides.**

That means the model is replaceable, while SYNAR remains the stable controller.

---

## Core architecture

```text
User
 ↓
SYNAR Core
 ├ Policy Layer
 ├ Routing Layer
 ├ Identity / Session Layer
 ├ Prompt Pipeline
 ├ Streaming Controller
 ├ Continuation Control
 ├ Runtime / Debug Layer
 ├ Memory Layer (planned)
 └ Learning Layer (planned)
 ↓
Model Interface
 ↓
Language Models
```

### Architectural rules

- SYNAR is the controller, not the model.
- Models must remain interchangeable.
- Infrastructure must stay separate from AI logic.
- `server.js` should remain infrastructure only.
- Core AI behavior should live in modular engine files.
- Long-term architecture is preferred over quick patching.

---

## Current implementation direction

SYNAR has been developed around a practical Node.js + Ollama stack with a modular backend direction.

### Current backend direction

- Node.js runtime
- Ollama as local model runtime
- modular AI logic in `core/`
- infrastructure separated from engine logic
- file-based logs for routing and runtime diagnostics

### Current operating concepts

- FAST / DEEP routing
- intent-aware model selection
- controlled streaming pipeline
- continuation handling for truncated outputs
- creator/admin-aware control direction
- local session control over external authentication

---

## Why SYNAR exists

Real model behavior in production-like conditions is often unstable.

During development, SYNAR was shaped by repeated system-level failures such as:

- streaming arriving as a single full response instead of chunks
- duplicated output caused by double aggregation
- long responses being cut off
- incorrect routing of complex requests into lightweight paths
- prompt growth causing latency and instability
- model behavior drift and identity leakage
- weak separation between system logic and model behavior

SYNAR exists to move those decisions out of fragile prompt-only behavior and into a controllable architecture layer.

---

## Engineering challenges solved

### 1. Streaming instability

Observed:
- delayed full-text delivery instead of chunked streaming
- broken real-time UX
- inconsistent Ollama chunk handling

Architectural response:
- stream adapter
- buffer layer
- chunk normalization
- single source of truth for streamed output

### 2. Output duplication

Observed:
- duplicated final responses after streaming
- backend and orchestrator both pushing content

Architectural response:
- removed secondary final reply push
- removed unsafe tail reconstruction logic
- enforced stream-first orchestration flow

### 3. Response cutoffs

Observed:
- incomplete long responses
- continuation flags failing to match actual output state

Architectural response:
- controlled continuation logic
- output-length aware handling
- reduced false continuation signals

### 4. Incorrect routing

Observed:
- long or analytical prompts falling into FAST paths
- multilingual intent detection breaking on fragile regex patterns

Architectural response:
- split `long_output_intent` from `deep_analysis_intent`
- moved toward `intent → policy → route`
- reduced dependence on brittle regex rules

### 5. Monolithic server pressure

Observed:
- too much AI logic drifting into infrastructure entrypoints
- increased maintenance risk

Architectural response:
- move core AI logic into modular engine files
- keep `server.js` focused on infrastructure responsibilities

---

## System modules

### Identity / Session Layer

SYNAR treats identity verification and system control as separate concerns.

Direction:
- Google OAuth and Email OTP can verify the user
- SYNAR keeps its own local session authority
- future admin/creator visibility should be decided by SYNAR, not by model compliance

### Routing Layer

Routing is built around the idea that response length and reasoning depth are not the same problem.

Direction:
- explicit mode override when needed
- DEEP path for analysis and long structured outputs
- FAST path for lightweight requests
- future confidence scoring

### Prompt Pipeline

Prompt assembly is treated as system infrastructure, not ad hoc prompting.

Direction:
- system rules
- identity rules
- verified session state
- language anchor
- chat history
- user input

### Streaming Controller

Streaming is treated as a first-class subsystem.

Direction:
- normalized chunk flow
- UI-safe buffering
- no duplicate aggregation
- stable chunk rendering path

### Continuation Control

Continuation should only happen when the output is actually incomplete.

Direction:
- detect real truncation
- avoid fake continuation states
- reduce hallucinated or forced endings

### Memory Layer (planned)

Future work is aimed at giving SYNAR memory as a controlled subsystem rather than letting the model blur prior context into unrelated replies.

### Learning Layer (planned)

The long-term goal is for SYNAR to learn from operation, corrections, routing outcomes, and quality signals without tying system intelligence to any single model.

---

## Development path

SYNAR has evolved through several practical phases:

1. initial infrastructure and Ollama connection
2. authentication layer with local session control
3. UI rebuild for chat streaming and session handling
4. server stabilization after migration to stronger hardware
5. modular backend restructuring
6. controlled continuation work
7. model strategy refinement around local model constraints
8. admin / creator-aware control direction
9. memory and learning layer planning

This matters because the project was not built as a static demo. It was shaped by debugging real behavior under changing runtime conditions.

---

## Current status

### Stable or mostly stabilized

- base UI flow
- local auth direction
- streaming path after fixes
- routing architecture direction
- modular core direction
- runtime logging direction

### Still actively evolving

- deeper routing reliability
- memory isolation
- creator/admin visibility rules
- long-output stability under load
- latency optimization
- learning layer implementation

---

## Roadmap

### Near-term

- finish routing stabilization
- harden continuation logic
- isolate memory from unrelated answers
- improve runtime telemetry
- keep infrastructure and AI logic separated cleanly

### Mid-term

- memory-aware routing
- confidence scoring for intent and route selection
- creator/admin control layer
- stronger observability for stream and route decisions

### Long-term

- SYNAR Memory Layer
- SYNAR Learning Layer
- model-agnostic policy governance
- deeper orchestration across interchangeable model backends

---

## Project value

SYNAR demonstrates practical work in:

- AI control-layer design
- LLM routing and orchestration
- streaming architecture
- debugging unstable real-time model behavior
- prompt/system boundary design
- backend modularization
- AI infrastructure thinking beyond a single model

---

## Author

**Artur Kucherenko**  
System architecture, AI control-layer design, routing logic, runtime debugging, and product direction.

**Website:** https://synar.dev  
**Email:** kucherenko1988artur1988@gmail.com

