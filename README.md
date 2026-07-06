<p align="center">
  <img src="logo.png" alt="SYNAR logo" width="180" />
</p>

# SYNAR

**Experimental multi-model AI orchestration system focused on reliability, transparency, and structured reasoning.**

SYNAR explores a practical question:

> Can multiple AI models work together more honestly and reliably than a single-model chatbot?

SYNAR is not designed as a simple chatbot wrapper. Its core idea is a **Parliament architecture**: a system layer where model roles, routing, consensus signals, storage, and decision logs remain separated instead of being hidden inside one prompt.

🌐 https://synar.dev  
✉️ kucherenko1988artur1988@gmail.com

---

## Current status

SYNAR is an active prototype. It has evolved from a local LLM chat interface into a modular AI orchestration platform with:

- multi-model orchestration;
- Parliament-style decision flow;
- early-stage consensus scoring;
- model adapters;
- persistent conversation and decision storage;
- runtime logging and development logs;
- a practical web UI for testing real model behavior.

This repository documents the architecture and development direction. Some live-server internals may be ahead of the public repository while the project is being cleaned and stabilized.

---

## What problem SYNAR explores

Modern LLM systems often fail in ways that are hard to detect:

- confident but unreliable answers;
- weak uncertainty handling;
- inconsistent behavior between models;
- fragile prompt-only control;
- poor separation between application logic and model behavior;
- silent failure when routing, memory, or context grows complex.

SYNAR moves part of the control out of fragile prompt behavior and into a structured orchestration layer.

> **The model generates. SYNAR coordinates, compares, stores, and decides how the system should proceed.**

---

## Core architecture

```text
User
 ↓
SYNAR API / Web UI
 ↓
Orchestration Layer
 ├─ Parliament Engine
 ├─ Consensus Engine
 ├─ Model Adapters
 ├─ History / Storage Layer
 ├─ Runtime Logs
 └─ Policy / Routing Logic
 ↓
Language Models
```

### Main components

- **Orchestration layer** — routes requests and coordinates model participation.
- **Parliament engine** — manages structured multi-model decision flow.
- **Consensus engine** — compares model outputs and estimates agreement signals.
- **Model adapters** — isolates API/model-specific logic from the core system.
- **History and storage layer** — stores conversations, decisions, and runtime data separately from model logic.
- **Web interface** — provides a practical chat UI and testing surface.

---

## Parliament architecture

The Parliament concept is the central design direction of SYNAR.

Instead of treating one model as the only source of truth, SYNAR is designed around separated model roles and system-level judgment. The goal is not to make models magically correct, but to expose disagreement, compare responses, and make the decision process visible.

Core principles:

- models must remain interchangeable;
- orchestration should be independent from any single provider;
- consensus should be logged, not hidden;
- uncertainty is a valid output;
- system logic should not live entirely inside prompts;
- history, routing, adapters, and consensus should remain separate modules.

---

## Consensus scoring

SYNAR includes an early-stage consensus mechanism that compares model responses and records agreement signals.

This is experimental. It does **not** claim to guarantee correctness or eliminate hallucinations.

Current goal:

- detect obvious divergence;
- compare response similarity;
- support future confidence scoring;
- create a transparent record of model agreement/disagreement.

Future direction:

- stronger semantic comparison;
- confidence thresholds;
- structured critique roles;
- adversarial model review;
- better evaluation datasets.

---

## Why this project matters

Most AI demos show successful outputs. SYNAR focuses on the harder part: what happens when model behavior is unstable, incomplete, contradictory, or overconfident.

During development, SYNAR was shaped by real system-level problems:

- streaming arriving as one delayed full response instead of chunks;
- duplicated output caused by double aggregation;
- long responses being cut off;
- incorrect routing of complex prompts into lightweight paths;
- growing context causing latency and instability;
- weak separation between system logic and model behavior;
- need for persistent logs and auditable decisions.

The project treats these failures as architectural data, not just bugs.

---

## Tech stack

- **Backend:** Node.js, Express
- **Storage:** SQLite
- **Frontend:** HTML, CSS, JavaScript
- **Deployment:** Linux server, nginx, Cloudflare
- **AI layer:** local and API-based LLM adapters
- **Runtime direction:** modular core with separated orchestration, adapters, storage, and UI

---

## Repository focus

This repository is intended to demonstrate:

- AI orchestration architecture;
- backend modularization;
- LLM API integration;
- model-agnostic system design;
- consensus and reliability experiments;
- QA-oriented thinking around failure cases;
- development discipline through logs and known-issue tracking.

---

## Documentation

Key documentation includes:

- `PARLIAMENT_ARCHITECTURE.md` — Parliament design and roles;
- `KNOWN_ISSUES.md` — active limitations and known problems;
- development logs — project evolution and implementation notes;
- engineering case notes — debugging and architectural decisions.

---

## Roadmap

### Near-term

- clean public repository structure;
- update documentation to match the live architecture;
- improve README and architecture diagrams;
- separate production code from backups and runtime data;
- add `.env.example` and stronger setup notes.

### Mid-term

- stronger semantic consensus logic;
- better test coverage;
- clearer model-role separation;
- improved telemetry and evaluation logs;
- UI improvements for multi-chat workflows and model visibility.

### Long-term

- advanced Parliament roles;
- memory-aware orchestration;
- confidence scoring;
- model-agnostic governance layer;
- stronger reliability testing framework.

---

## Important note

SYNAR is an experimental project. It is not presented as a finished commercial AI product or a correctness guarantee.

Its value is in exploring architecture, reliability, model collaboration, transparent decision flow, and practical AI system debugging.

---

## Author

**Artur Kucherenko**  
🌐 https://synar.dev  
✉️ kucherenko1988artur1988@gmail.com
