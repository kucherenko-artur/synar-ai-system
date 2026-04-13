<p align="center">
  <img src="logo.png" alt="SYNAR logo" width="180" />
</p>

                                             # SYNAR
**AI control and routing layer where models remain interchangeable and the system stays in control.**
> This project focuses on debugging real AI system behavior, not just building around models.

🌐 https://synar.dev  
✉️ kucherenko1988artur1988@gmail.com  

---

## ⚡ What problem SYNAR solves

Modern LLM-based systems break in predictable ways:

- streaming is inconsistent or delayed  
- long responses get cut off  
- routing decisions fail under complexity  
- prompt growth causes latency spikes  
- system logic leaks into model behavior  

SYNAR moves control out of fragile prompt behavior into a structured system layer.

---

## 🧠 What SYNAR is

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

> **The model generates. SYNAR decides.**

That means the model is replaceable, while SYNAR remains the stable controller.

---

## 🏗 Core architecture

### Quick view

```
User
  |
  v
SYNAR Core
  |
  v
Control Layers (Policy / Routing / Runtime)
  |
  v
Model Interface
  |
  v
Language Models
```

### Full system

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

---

## 🧩 Architectural rules

- SYNAR is the controller, not the model.
- Models must remain interchangeable.
- Infrastructure must stay separate from AI logic.
- `server.js` should remain infrastructure only.
- Core AI behavior should live in modular engine files.
- Long-term architecture is preferred over quick patching.

---

## ⚙️ Current implementation direction

SYNAR has been developed around a practical Node.js + Ollama stack with a modular backend direction.

### Backend direction

- Node.js runtime
- Ollama as local model runtime
- modular AI logic in `core/`
- infrastructure separated from engine logic
- file-based logs for routing and runtime diagnostics

### Operating concepts

- FAST / DEEP routing
- intent-aware model selection
- controlled streaming pipeline
- continuation handling for truncated outputs
- creator/admin-aware control direction
- local session control over external authentication

---

## 🔥 Why SYNAR exists

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

## 🛠 Engineering challenges solved

### 1. Streaming instability

**Observed**
- delayed full-text delivery instead of chunked streaming
- broken real-time UX
- inconsistent Ollama chunk handling

**Architectural response**
- stream adapter
- buffer layer
- chunk normalization
- single source of truth for streamed output

---

### 2. Output duplication

**Observed**
- duplicated final responses after streaming
- backend and orchestrator both pushing content

**Architectural response**
- removed secondary final reply push
- removed unsafe tail reconstruction logic
- enforced stream-first orchestration flow

---

### 3. Response cutoffs

**Observed**
- incomplete long responses
- continuation flags failing to match actual output state

**Architectural response**
- controlled continuation logic
- output-length aware handling
- reduced false continuation signals

---

### 4. Incorrect routing

**Observed**
- long or analytical prompts falling into FAST paths
- multilingual intent detection breaking on fragile regex patterns

**Architectural response**
- split intent layers
- moved toward `intent → policy → route`
- reduced dependence on brittle regex rules

---

### 5. Monolithic server pressure

**Observed**
- too much AI logic drifting into infrastructure entrypoints
- increased maintenance risk

**Architectural response**
- move core AI logic into modular engine files
- keep `server.js` focused on infrastructure responsibilities

---

## 🧠 System modules

### Identity / Session Layer

- Google OAuth and Email OTP verify user
- SYNAR maintains its own session authority
- future admin/creator visibility handled by system

---

### Routing Layer

- explicit override support
- DEEP path for analysis
- FAST path for lightweight tasks
- future confidence scoring

---

### Prompt Pipeline

- system rules
- identity rules
- session state
- language anchor
- history
- user input

---

### Streaming Controller

- normalized chunk flow
- UI-safe buffering
- no duplicate aggregation
- stable rendering path

---

### Continuation Control

- detect real truncation
- avoid fake continuation
- prevent forced endings

---

### Memory Layer (planned)

Controlled memory subsystem instead of implicit model memory.

---

### Learning Layer (planned)

System-level learning independent from specific models.

---

## 📈 Development path

1. infrastructure + Ollama
2. authentication layer
3. UI + streaming fixes
4. server stabilization
5. modular backend
6. continuation logic
7. routing refinement
8. creator control direction
9. memory + learning planning

---

## 📊 Current status

### Stable

- UI
- authentication
- base routing
- logging
- modular direction

### In progress

- routing reliability
- memory isolation
- creator visibility
- long-output stability
- latency optimization
- learning layer

---

## 🛣 Roadmap

### Near-term

- routing stabilization
- continuation hardening
- telemetry improvements

### Mid-term

- memory-aware routing
- confidence scoring
- admin layer

### Long-term

- SYNAR Memory Layer
- SYNAR Learning Layer
- model-agnostic governance
- advanced orchestration

---

## 💡 Project value

SYNAR demonstrates:

- AI control-layer design
- LLM orchestration
- streaming architecture
- debugging real model behavior
- prompt/system boundary design
- backend modularization
- system-level AI thinking

---

## 🔬 Engineering Cases

Real system debugging and architectural decisions are documented here:

➡️ [SYNAR Engineering Challenges](./SYNAR_ENGINEERING_CASES.md)

---

## 👤 Author

**Artur Kucherenko**  
🌐 https://synar.dev  
✉️ kucherenko1988artur1988@gmail.com
