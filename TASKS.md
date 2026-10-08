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
- [x] Add five website-specific examples with source and gallery-rights evidence; bundled asset rights remain unverified.
- [x] Implement explainable metadata matching, rationale, and avoid-for display.
- [x] Add fixture briefs for business, portfolio, editorial, lightweight pages, and no-match input.
- [x] Verify accessibility/interaction fields, rationale, provenance pointers, and MCP protocol behavior.

### M3 follow-up — website relevance improvement
- [x] Capture baseline outputs for both real-site cases; test no-fit and conflicting constraints (`docs/research/2026-10-08-recommendation-baseline.md`, `tests/test_server.py`).
- [x] Implement deterministic purpose/constraint-aware ranking and `avoid_for` handling; test justified no-fit behavior.
- [x] Review bookmark leads and verify a small reference set with dated per-item provenance and rights fields; keep uncleared assets out of reuse advice (`docs/research/2026-10-08-bookmark-reference-review.md`).
- [x] Return distinct website, component and slide-deck reference types with grounded design cues and additive resource metadata.
- [x] Compare before/after relevance; run 26 tests and live stdio MCP discovery/calls/resource reads. Owner expressed no visual preference yet; no direction is designated preferred.

## M4 — Read-only HTML page review (complete)
- [x] Specify allowed-root, selected-path, 1 MB size limit, and resolved-path traversal behavior.
- [x] Add inert parsing and evidence-bearing findings for semantic, responsive, and accessibility signals.
- [x] Add compliant, defective/hostile, malformed, and oversized-file tests/fixtures.
- [x] Verify no execution, writes, or access outside the audit root; label heuristic limits.

## M5 — MCP client protocol smoke
- [x] Direct MCP SDK smoke: discover five tools/two resources, call every tool, read both resources.
- [x] Keep client-specific registration outside the project contract; document the stdio launch command in README.

## Deferred pending explicit approval
- [ ] Remote crawling, template downloads/import, writes into user projects, browser-based audits, HTTP/LAN transport, authentication, and deployment.

## M6 — Owner-requested local design evaluation
- [x] Inspect the public Stephen Phillips homepage and derive a page brief from visible business content.
- [x] Run the actual MCP recommender; record its candidate relevance and licensing caveats.
- [x] Build a local-only standalone homepage concept in `evaluations/stephenphillips-v1/` without modifying the live site or sibling projects.
- [x] Run `audit_local_html` and inspect desktop/mobile rendering and basic responsive/keyboard signals.
- [x] Obtain an independent critique; remove unverified project/location claims, restore omitted services, and confirm the full hero rendering.
- [x] Reuse one image from the existing homepage gallery by source URL and add two dated public reviews with reviewer attribution.
- [x] Fix owner-reported testimonial date contrast/alignment and align work-row copy; verify at desktop and mobile sizes.
- [x] Owner authorized including this evaluation in the public repository; retain source links and reviewer attribution, and label the image and reviews as material from the current public site rather than original project assets.
- [ ] Get owner/representative feedback and test an alternative design direction before claiming the redesign is preferred.
- [x] Improve MCP candidate ranking based on both observed mismatches; current brief comparison and limits are recorded in `docs/research/2026-10-08-recommendation-baseline.md`.
- [x] Repeat the local-only evaluation with HappyMonkey.AI at the owner's request; record actual MCP output, prototype and checks in `evaluations/happymonkey-v1/`.

## M7 — Public repository preparation
- [x] Add the repository MIT license and state its scope alongside third-party provenance caveats.
- [x] Add a fictional editorial example that demonstrates general recommendation behavior without using client material.
- [x] Remove machine-specific workspace paths and client-specific MCP setup history from tracked project documentation.
- [x] Run the full suite with a writable pytest temp root: 26 passed; `git diff --check` passed.
- [x] Confirm the target repository identity and receive owner authorization to publish the reviewed snapshot publicly through GitHub CLI.
