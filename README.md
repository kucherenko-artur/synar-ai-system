<p align="center">
  <img src="logo.png" width="220"/>
</p>

<p align="center">
  <b>AI Orchestration • Routing • Streaming • Control Layer</b>
</p>
# 🚀 SYNAR — AI Orchestration System

> Built by **Artur Kucherenko**  
> AI Systems • QA • Model Evaluation • Debugging

🔗 **Live Project / Repo:**  
- https://github.com/kucherenko-artur/synar-ai-system  
- https://github.com/kucherenko-artur/Artur-Kucherenko-QA  
- https://synar.dev
---

## 💡 What is SYNAR

SYNAR is not a chatbot.

It is an **AI orchestration system** that controls:
- how models are selected
- how responses are generated
- how output is delivered in real time

Instead of relying on a single model, SYNAR introduces a structured pipeline:
                        intent → policy → route


This allows the system to distinguish between:
- long-form responses  
- deep analytical reasoning  

---

## 🧠 Why This Project Matters

During development, multiple real-world AI issues were discovered:

- responses were getting cut off  
- streaming was unstable  
- models produced inconsistent outputs  
- simple models handled complex reasoning incorrectly  

Instead of patching issues individually, the system was redesigned into a **controlled architecture layer above LLMs**.

---

## ⚙️ Core Architecture

### 🔹 Orchestrator
Controls the full lifecycle of each request:
- input processing  
- routing decisions  
- response streaming  

---

### 🔹 Intent Layer

Detects request type before execution:

- `long_output_intent` → long-form response  
- `deep_analysis_intent` → reasoning required  

---

### 🔹 Routing System

Priority:

1. explicit mode  
2. deep_analysis → DEEP model  
3. long_output → DEEP model  
4. fallback → FAST model  

---

### 🔹 Streaming Pipeline

Custom-built to support:
- real-time chunk delivery  
- buffering  
- stable UI updates  

---

## 🔥 Engineering Scope (What I Actually Did)

### 🧪 AI Behavior Analysis & QA

- Investigated unstable model behavior across languages  
- Compared FAST vs DEEP outputs  
- Identified logical inconsistencies in responses  
- Evaluated model quality under different conditions  

---

### ⚡ Streaming & Real-Time Debugging

- Fixed broken streaming (no chunks, delayed output)  
- Solved response duplication (double aggregation bug)  
- Eliminated response cutoffs in long outputs  
- Built stable streaming pipeline  

---

### 🧭 Routing & System Design

- Designed intent-based routing system  
- Separated **response length vs reasoning complexity**  
- Replaced fragile regex logic (multilingual issues)  
- Built structured decision pipeline  

---

### 🖥️ Frontend & UI

- Built UI from scratch  
- Implemented real-time streaming rendering  
- Connected frontend to backend orchestration layer  
- Handled async state and response flow  

---

### 🛠️ Infrastructure & Deployment

- Configured nginx + HTTPS  
- Managed systemd services  
- Worked with Cloudflare caching issues  
- Maintained production-like environment  

---

## 🧩 Key Problems Solved

### ❌ Streaming Failure → ✅ Real-Time Responses  
### ❌ Response Duplication → ✅ Clean Output  
### ❌ Response Cutoffs → ✅ Stable Long Answers  
### ❌ Wrong Routing → ✅ Intent-Based Model Selection  

---

## 📊 What This Demonstrates

This project shows:

- Ability to debug real AI system behavior  
- Understanding of model limitations  
- Designing control layers above LLMs  
- Working with unstable real-time systems  
- Full-stack integration (UI ↔ backend ↔ models)  

---

## 📌 Current Status

✔ Streaming stabilized  
✔ Routing system working  
✔ Output consistency improved  
✔ System ready for expansion  

---

## 🔮 Next Steps

- memory-aware routing  
- intent confidence scoring  
- lightweight intent classifier  

---

## 👤 Author

**Artur Kucherenko**  
AI QA • AI Systems • Debugging • Model Evaluation  

📫 Open to:
- AI Training roles  
- AI Evaluation roles  
- QA / Testing (AI systems)  

---


