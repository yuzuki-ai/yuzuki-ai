# yuzuki-ai

A memory-persistent companion system.

---

## What This Is

Not a product. A system that remembers. Built for long-form interaction where context persists across sessions.

The architecture treats memory as primary, not an add-on. Embeddings stored in pgvector. Episodic and semantic layers separate but linked.

---

## Implementation

| Version | Stack | Status |
|---------|-------|--------|
| [v1](https://github.com/icedeyes12/yuzu-companion) | Flask · SQLAlchemy · ChaCha20-Poly1305 · Rich TUI | Public, stable |
| [v2](https://github.com/icedeyes12/yuzu-v2) | FastAPI · psycopg2 · pgvector · ONNX Runtime · bcrypt · WebSocket | Private, WIP |

**v2 features:** 43 AI models across 4 providers (Ollama · OpenRouter · Chutes · Zo), ~1.5GB memory footprint, deduplication >0.95 similarity.

---

## Architecture (v2)

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Web UI    │────▶│  FastAPI    │────▶│ PostgreSQL  │
│  (future)   │     │   Backend   │     │  + pgvector │
└─────────────┘     └─────────────┘     └─────────────┘
                            │
                            ▼
                     ┌─────────────┐
                     │ ONNX Runtime│
                     │  (embed)    │
                     └─────────────┘
```

- **Storage**: PostgreSQL 16 + pgvector (semantic + episodic)
- **Inference**: ONNX Runtime, multilingual-e5-base, 768-dim
- **Auth**: bcrypt (12 rounds) + JWT + slowapi rate limiting
- **AI Providers**: Ollama, OpenRouter, Chutes, Zo API

---

## Origin

Built by [icedeyes12](https://github.com/icedeyes12). Single-developer system, phone-first workflow (Termux → Supabase → self-hosted).

Core idea: continuity over scale.

---

## State (v2)

| Component | Status |
|-----------|--------|
| Backend API | ✓ Stable |
| Auth system | ✓ bcrypt + rate limiting |
| Memory system | ✓ Deduplication + ranking |
| Embeddings | ✓ ONNX ~1.5GB |
| WebSocket chat | ✓ Streaming |
| Frontend | ○ Not started |
| Voice/TTS | ○ Planned |

---

<p align="center">
  <sub>creator: <a href="https://github.com/icedeyes12">icedeyes12</a> · v1: <a href="https://github.com/icedeyes12/yuzu-companion">yuzu-companion</a> · v2: <a href="https://github.com/icedeyes12/yuzu-v2">yuzu-v2</a></sub>
</p>