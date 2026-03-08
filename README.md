# yuzuki-ai

A memory-persistent companion system.

---

## What This Is

Not a product. A system that remembers. Built for long-form interaction where context persists across sessions.

The architecture treats memory as primary, not an add-on. Embeddings stored in pgvector. Episodic and semantic layers separate but linked. Runtime on ONNX for local-first inference.

---

## Implementation

This repository documents the system identity and architecture. The actual implementation lives here:

→ **[github.com/icedeyes12/yuzu-companion](https://github.com/icedeyes12/yuzu-companion)** (v1, public)

v2 is currently under construction in private.

---

## Architecture

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Web UI    │────▶│  FastAPI    │────▶│ PostgreSQL  │
│  (React)    │     │   Backend   │     │  + pgvector │
└─────────────┘     └─────────────┘     └─────────────┘
                            │
                            ▼
                     ┌─────────────┐
                     │ ONNX Runtime│
                     │  (embed)    │
                     └─────────────┘
```

- **Storage**: PostgreSQL 16 + pgvector (semantic + episodic)
- **Inference**: ONNX Runtime, multilingual-e5-base
- **API**: FastAPI + psycopg2
- **Interface**: Web primary, CLI for maintenance

---

## Origin

Built by [icedeyes12](https://github.com/icedeyes12). Single-developer system, phone-first workflow (Termux → Supabase → self-hosted migration).

Core idea: continuity over scale.

---

## State

| Component | Status |
|-----------|--------|
| Memory system | ✓ Active |
| Embedding pipeline | ✓ Active |
| Auth layer | ✓ Active |
| Web frontend | ○ In progress |
| Voice integration | ○ Planned |

---

<p align="center">
  <sub>creator: <a href="https://github.com/icedeyes12">icedeyes12</a> · implementation: <a href="https://github.com/icedeyes12/yuzu-companion">yuzu-companion</a></sub>
</p>