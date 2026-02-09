# Glossary (Repo Excerpt)

For the full glossary, see: https://github.com/instance001/Whatisthisgithub/blob/main/GLOSSARY.md

This file contains only the glossary entries for this repository. Mapping tag legends and global notes live in the full glossary.

## 4roomciv
| Term | Alternate term(s) | Alt map | External map | Relation to existing terminology | What it is | What it is not | Source |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 4-Room Civilization MVP | 4roomciv | ~ | ∅ | No established external analogue; internal pilot architecture name | Small trial (2–3 humans, 1–2 local LLMs) integrating Helix memory with a paired room (R3) and a minimal Commons (R4) | Not a production-scale deployment or cloud multi-tenant system; limited to R3/R4 scope | 4roomciv/README.md |
| Helix memory | Helix | ~ | ~ | Partial match to full-text information retrieval store (SQLite FTS5); structured memory layer | Memory subsystem behind /helix endpoints storing spines; search via FTS5 with topics exact-matched via child table | Not described as a vector-embedding store or raw transcript log | 4roomciv/README.md |
| Spine (Helix Spine v1) | spine, spines | = | ~ | Structured claim/rationale record; akin to a typed fact entry | JSON object with spine_id, timestamp_utc, topic[1–4], claim (≤280 chars), rationale (≤320), optional evidence_refs, stance_vector, links, tags, notes_short, confidence [0,1], version=1 | Not freeform notes; required fields and length bounds apply; not versioned beyond v1 | 4roomciv/4room-civ-mvp.zip:schemas/helix_spine.schema.json |
| Paired Room (R3) | paired room, R3 | = | ~ | Partial analogue to a dyadic session channel | Endpoint `/paired/session/generate` that runs RAG→LLM→messages→auto-extract spines for a paired setting | Not a shared commons; not multi-party broadcast | 4roomciv/README.md |
| Commons (R4) | commons | = | ~ | Matches a shared threaded discussion board | Endpoints `/commons/threads`, `/commons/threads/{id}/post` for communal threads | Not a memory spine store; not described as moderated/ACL-gated | 4roomciv/README.md |
| SPINE_AUTOWRITE | SPINE_AUTOWRITE=0 | = | ~ | Configuration toggle | Env var controlling automatic spine writes; set to 0 to disable autowrite | Not affecting manual `/helix/spines` writes or search behavior | 4roomciv/README.md |
| Helix search endpoints | /helix/search, /helix/recent, /helix/topic/{slug} | = | ~ | Standard REST-style retrieval APIs | Read endpoints for querying Helix memory (full-text search, recency, topic) | Not write interfaces; not guaranteed to return embedding similarity | 4roomciv/README.md |
| Commons thread endpoints | /commons/threads, /commons/threads/{id}/post | = | ~ | Standard REST thread APIs | CRUD-like interfaces for creating and posting to commons threads | Not connected to spine schema; no auto-extraction of spines implied | 4roomciv/README.md |
| Metrics dashboard endpoint | /metrics/dashboard | = | ~ | Standard monitoring endpoint analogue | Read-only endpoint exposing metrics dashboard | Not documented as writable or for control | 4roomciv/README.md |
