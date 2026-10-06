# Development tasks

Status legend: `[x]` verified complete; `[ ]` not started. Keep this execution board aligned with `ROADMAP.md` and `SPEC.md`.

## M0 — Working baseline (complete)
- [x] Create the read-only stdio MCP project and package metadata.
- [x] Add local template search, project inventory, design guidance, and two resources.
- [x] Add 17 unit tests covering index, recommendations, and HTML review behavior.
- [x] Exercise MCP stdio discovery, resource listing, and representative tool call.

## M1 — Reliable local catalog (complete)

### M1.1 Configuration and data contract
- [x] Define configurable workspace/index paths with safe workspace-relative defaults (`src/html_design_advisor/server.py`).
- [x] Validate index schema/version, root shape, required record fields, and file size; fail closed on invalid inputs.
- [x] Document environment/configuration, read-only boundary, and error behavior (`README.md`, `CONTEXT.md`).

### M1.2 Resilience and matching
- [x] Test valid, missing, malformed, invalid-schema, oversized, outside-root, and empty indexes (`tests/test_server.py`).
- [x] Test safe empty responses when the index is unreadable or malformed.
- [x] Clamp search limits at both edges and test them.
- [x] Define deterministic tie-breaking; test repeated query results are stable.

### M1.3 Boundary and protocol acceptance
- [x] Keep lookup to configured catalog path and the direct curated reference list; no dependency traversal.
- [x] Run `.venv/Scripts/python.exe -m pytest -q` (16 passed) and `git diff --check`.
- [x] Use an MCP client to re-check tool/resource discovery and representative tool/resource readback.
- [x] Review SPEC acceptance and resolve local-catalog gaps.

## M2 — Evidence-backed source catalog (after M1)
- [ ] Verify canonical URLs and official terms/license evidence for each candidate source.
- [ ] Add dated evidence notes under `docs/research/` with source scope, attribution, commercial-use conditions, and unknowns.
- [ ] Add evidence references and verification status to resource records; keep unknown license status non-reusable.
- [ ] Add tests preventing unknown or expired evidence from yielding reuse approval.

## M3 — Brief-to-design recommendations (local reference slice complete; catalog expansion awaits M2)
- [x] Define brief inputs and response contract in `SPEC.md` and MCP tool schema.
- [ ] Add website-specific examples only when source provenance/license evidence is available; current catalog is slide decks.
- [x] Implement explainable metadata matching, rationale, and avoid-for display.
- [x] Add fixture briefs for business, portfolio, editorial, lightweight pages, and no-match input.
- [x] Verify accessibility/interaction fields, rationale, provenance pointers, and MCP protocol behavior.

## M4 — Read-only HTML page review (complete)
- [x] Specify allowed-root, selected-path, 1 MB size limit, and resolved-path traversal behavior.
- [x] Add inert parsing and evidence-bearing findings for semantic, responsive, and accessibility signals.
- [x] Add compliant, defective/hostile, malformed, and oversized-file tests/fixtures.
- [x] Verify no execution, writes, or access outside the audit root; label heuristic limits.

## M5 — Optional MCP client integration
- [x] Save/read back Hermes default-profile stdio configuration; record machine-local evidence in ignored `MCP.local.md`.
- [x] Direct MCP SDK smoke: discover five tools/two resources, call every tool, read both resources.
- [ ] Fix Hermes-native MCP test blocker (`tools.mcp_tool.StdioServerParameters` missing) without modifying shared Hermes dependencies unless authorized.

## Deferred pending explicit approval
- [ ] Remote crawling, template downloads/import, writes into user projects, browser-based audits, HTTP/LAN transport, authentication, and deployment.