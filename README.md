<p align="center">
  <img src="logo.png" width="180"/>
</p>

# SYNAR

**AI Control and Routing Layer where models are interchangeable and the system remains the controller.**

🌐 Website: https://synar.dev

---

## 🧠 Core Idea

SYNAR is not a chatbot and not tied to a single model.

It is a **control layer above language models** that manages:

- model routing
- prompt construction
- streaming behavior
- continuation logic
- session identity
- system-level decisions

> Models generate.  
> SYNAR decides.

---

## 🏗 Architecture

```
User
  |
  v
SYNAR Core
  |
  v
Policy Layer
  |
  v
Routing Layer
  |
  v
Model Interface
  |
  v
Language Models (Ollama / future adapters)
```

---

## ⚙️ System Structure

```
/opt/synar

- server.js           (infrastructure layer only)

- core/
  - synar-engine.js
  - routing/
  - prompt/
  - streaming/
  - identity/

- logs/
  - synar-app.log
  - synar-error.log
  - synar-routing.log
```

---

## 🤖 Models

Current setup (Ollama):

- FAST route → qwen2.5:3b-instruct  
- DEEP route → qwen3:4b-instruct  

Routing is handled by SYNAR, not the model.

---

## 🔄 Prompt Pipeline

Prompt is constructed in layers:

1. Core rules  
2. Identity rules  
3. Session verification  
4. Language anchor  
5. Chat history  
6. User input  

---

## 🌊 Streaming System

SYNAR implements controlled streaming over Ollama.

Key features:

- chunk handling  
- response buffering  
- latency tracking  
- controlled continuation  

---

## 📊 Current System State

Stable:

- UI layer  
- Authentication (Google OAuth + JWT)  
- Basic routing  
- Logging system  

In progress:

- streaming stability  
- continuation detection  
- prompt optimization  
- creator/debug control layer  

---

## 🔥 Engineering Challenges & Solutions

### Unstable Streaming
Buffer layer + controlled output

### Response Cutoffs
Continuation detection logic

### Wrong Routing
Routing refinement

### Large Prompt
Compression + caching

### Server vs Model Responsibility
Moving logic to server layer

---

## 🛣 Roadmap

- Memory Layer  
- Creator Debug Layer  
- Confidence-based routing  
- Model abstraction layer  
- Diagnostics layer  

---

## 👤 Author

Artur Kucherenko  
Email: kucherenko1988artur1988@gmail.com  
Website: https://synar.dev
