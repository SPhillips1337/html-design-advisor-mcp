# Development tasks

Status legend: `[x]` verified complete; `[ ]` pending. Keep this execution board aligned with `ROADMAP.md` and `SPEC.md`.

## M0 — Working baseline (complete)
- [x] Create the read-only stdio MCP project and package metadata.
- [x] Add local template search, project inventory, design guidance, and two resources.
- [x] Add 18 unit tests covering index, recommendations, source metadata, and HTML review behavior.
- [x] Exercise MCP stdio discovery, all five tool calls, and both resource reads.

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
- [x] Run `.venv/Scripts/python.exe -m pytest -q` (18 passed) and `git diff --check`.
- [x] Use an MCP client to re-check tool/resource discovery and representative tool/resource readback.
- [x] Review SPEC acceptance and resolve local-catalog gaps.

## M2 — Evidence-backed source catalog (provider-level evidence complete; item-level rights unknown)
- [x] Verify and record canonical source URLs and available official provider-level terms/license evidence; label snippet-only evidence where applicable.
- [x] Add dated evidence notes under `docs/research/` with source scope, attribution, commercial-use conditions, and unknowns.
- [x] Add evidence references and verification status to source records; keep specific template/bundled-asset status unverified.
- [x] Test that source records and recommendations preserve unknown per-asset license status rather than approving reuse.

## M3 — Brief-to-design recommendations (local reference slice complete; relevance limitations found)
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

## M6 — Owner-requested local design evaluation
- [x] Inspect the public Stephen Phillips homepage and derive a page brief from visible business content.
- [x] Run the actual MCP recommender; record its candidate relevance and licensing caveats.
- [x] Build a local-only standalone homepage concept in `evaluations/stephenphillips-v1/` without modifying the live site or sibling projects.
- [x] Run `audit_local_html` and inspect desktop/mobile rendering and basic responsive/keyboard signals.
- [x] Obtain an independent critique; remove unverified project/location claims, restore omitted services, and confirm the full hero rendering.
- [x] Reuse one image from the existing homepage gallery by source URL and add two dated public reviews with reviewer attribution.
- [ ] Confirm image/client-asset rights and current testimonial/attribution status before any public release.
- [ ] Get owner/representative feedback and test an alternative design direction before claiming the redesign is preferred.
- [ ] Improve MCP candidate ranking based on the observed mismatch (Daisy Days/BlockFrame/Broadside for a freelance-business homepage).
- [ ] Repeat with happymonkey.ai only after the first evaluation is reviewed.