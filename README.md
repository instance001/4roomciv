# 4-Room Civilization — MVP (Helix + LM Studio)

**Goal:** small trial (2–3 humans, 1–2 local LLMs) with Helix memory, a paired room (R3), and a minimal Commons (R4).

## Quickstart
1) `pip install -r requirements.txt`
2) In LM Studio: enable Local Server (OpenAI-compatible)
   ```powershell
   $env:LM_API_BASE="http://127.0.0.1:1234"
   $env:LM_MODEL="Hermes-2-Mistral-7B-GGUF"
   ```
3) Run API: `uvicorn main:app --reload --port 8080`
4) Token:
   ```bash
   curl -s -X POST http://127.0.0.1:8080/auth/anon -H "Content-Type: application/json" -d "{"proof":"ok"}"
   ```
5) Try: `GET /helix/recent`, `GET /helix/search?q=memory`

## Endpoints
- `POST /paired/session/generate` – RAG→LLM→messages→auto-extract spines
- `POST /helix/spines` – write spines (validated)
- `GET /helix/search` | `GET /helix/recent` | `GET /helix/topic/{slug}`
- `GET /commons/threads` | `POST /commons/threads` | `POST /commons/threads/{id}/post`
- `GET /metrics/dashboard`

## Notes
- Set `SPINE_AUTOWRITE=0` to disable auto writes.
- SQLite FTS5 backs search; topics exact-match via child table.
