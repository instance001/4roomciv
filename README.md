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

# Relicensing Notice

**Effective Date:** 30 november 2025  
**New License:** GNU Affero General Public License v3.0 (AGPL-3.0)  
**Previous License:**  CC-BY-SA 4.0

---

## Summary

This project has been fully relicensed under the **GNU Affero General Public
License v3.0 (AGPLv3)**. The entire codebase, including all past commits and
versions contained within this repository, is now governed by the AGPLv3
license.

I am the **sole copyright holder** of all code and assets in this repository.
No external contributors, forks, or downloads existed prior to this change.
Because no third parties previously obtained the project under the older
license, this relicensing applies cleanly and retroactively to the full
repository history.

---

## Why AGPLv3?

AGPLv3 ensures that:

- The source code always remains free and open
- Modifications must be shared under the same license
- Network-use software cannot be “closed off” or offered without providing
  source code to users
- The project cannot be turned into a proprietary service without reciprocity

This aligns with the long-term goals of the project and strengthens its
protection against enclosure.

---

## Scope of Relicensing

This relicensing applies to:

- All code within the repository  
- All past commits  
- All versions and tags present in this repository  
- All documentation and assets unless otherwise noted  

Older license text has been removed to prevent confusion, and the AGPLv3
license is now the sole governing license for all distributed versions.

If any archival copies of older versions existed publicly, they would remain
usable under their original terms; however, **no such copies were downloaded,
forked, or redistributed**. Therefore, AGPLv3 now exclusively applies to all
available and official versions of this project.

---

## Where to Find the License

The full AGPLv3 license text is included in the repository.
