# yuzuki-ai

A memory-persistent companion system.

---

## What This Is

Not a product. A system that remembers. Built for long-form interaction where context persists across sessions.

The architecture treats memory as primary, not an add-on. Embeddings stored in pgvector. Episodic and semantic layers separate but linked. Runtime on ONNX for local-first inference.

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

## Related

- Creator: [github.com/icedeyes12](https://github.com/icedeyes12)

---

<p align="center">
  <sub>memory-first · local-possible · continuity-obsessed</sub>
</p>