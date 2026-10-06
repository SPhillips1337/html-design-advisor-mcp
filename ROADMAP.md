# Development roadmap

Product goal: a local, read-only MCP advisor that helps an AI client choose and review HTML page designs using the user's brief, local design references, and source/license evidence.

Status: M0, M1, M2 provider-source research, and M4 are implemented and verified. M3's local reference recommender is implemented; website-specific catalog expansion remains constrained by per-asset license uncertainty. Hermes registration was saved/read back for M5, but its native MCP test is blocked by an Hermes-side SDK import/attribute error. The active Hermes dependency environment was not modified. Roadmap items do not authorize template downloads, project writes, or deployment.

## Milestone 0 — Working baseline (complete)

- [x] Create Python stdio MCP project.
- [x] Expose local template search, local reference inventory, and design guidance.
- [x] Add source and local-assets MCP resources.
- [x] Add initial unit tests and verify live MCP discovery/tool invocation.

Exit evidence: 18 tests pass; MCP client discovers five tools and two resources, calls every tool, and reads both resources.

## Milestone 1 — Reliable local catalog (complete)

Goal: make catalog results predictable, bounded, configurable, and safe under missing or malformed files.

1. Make workspace/catalog roots explicitly configurable; retain current workspace-relative defaults.
2. Define and validate the index schema and record required fields.
3. Add fixtures for valid, missing, malformed, invalid-schema, and empty indexes.
4. Clamp limits and specify deterministic ranking/tie-break behavior; prove it in tests.
5. Keep scans restricted to the configured curated directories; test that dependency trees and unrelated siblings are not traversed.
6. Update README and CONTEXT with setup, configuration, filesystem boundaries, and error behavior.
7. Verify V0 unit suite, V1 boundary/schema review, V2 malformed-input tests, and V3 MCP client calls/resource reads.

Exit evidence: 18-test suite includes malformed/missing/wrong-schema/count-mismatch/duplicate-slug/oversized/outside-root/empty index cases, bounded search and deterministic order; live MCP discovery and calls passed. Catalog and audit roots are configured separately; no sibling code was changed.

## Milestone 2 — Evidence-backed source catalog (provider terms verified; item rights unverified)

Goal: make external source entries useful without overstating their content or reuse rights.

1. Verify each candidate's canonical URL and current official license/terms page.
2. Record dated evidence, exact license scope (site-level vs individual item), attribution obligations, commercial-use restrictions, and uncertainty in `docs/research/`.
3. Separate verified facts from user-provided claims and derived recommendations.
4. Add source records with explicit verification date and evidence URL; do not infer that a site's general terms cover every template.
5. Add tests that missing/expired/unknown license evidence never becomes a “safe to reuse” recommendation.

Exit evidence: dated research covers provider terms and license pages for html.design, Colorlib, TemplateMo, uiCookies (official search result only), W3.CSS, dawidolko/Website-Templates, and the local beautiful-html-templates repository. Source registry distinguishes checked provider terms from unverified per-asset rights; recommendations do not mark assets cleared for reuse. No templates were downloaded or redistributed.

## Milestone 3 — Brief-to-design recommendations (initial local slice implemented)

Goal: return useful and explainable candidate directions for an actual webpage brief.

1. Define an input contract for page purpose, audience, content, mood, framework constraints, accessibility needs, and required interactions.
2. Extend local metadata with website-oriented references only where their provenance/license is known; label slide-deck examples as such.
3. Implement candidate scoring with clear rationale and disqualifying constraints; avoid pretending keyword overlap is design judgment.
4. Return a compact design brief: recommended direction, palette/type/layout cues, matching references, caveats, and next steps.
5. Test multiple fixture briefs (business landing page, portfolio, editorial, minimal lightweight page) including empty/ambiguous input.
6. Independently review the responses against SPEC acceptance and verify MCP tool discovery/calls.

Exit criteria: responses explain why each candidate fits, identify evidence and limitations, respect explicit user constraints, and keep licensing separate from visual suitability.

## Milestone 4 — Read-only HTML page review (implemented)

Goal: inspect a user-selected local HTML file for design implementation signals without executing it.

1. Define explicit path consent and allowed-root rules before any file-reading tool is exposed.
2. Parse content as inert text; never launch a browser or execute scripts in this milestone.
3. Add bounded checks for semantic landmarks, titles/headings, image alt text, viewport metadata, responsive CSS indicators, focus styles, and reduced-motion handling.
4. Return findings with file/line evidence where feasible, severity, confidence, and limitations; do not claim a complete WCAG audit.
5. Add fixtures for compliant, common-defect, malformed, oversized, and hostile instruction/script examples.
6. Verify path traversal/symlink policy and enforce size/time bounds.

Exit evidence: fixture tests and live MCP call confirm bounded inert parsing, outside-root/oversized rejection, line evidence, and caveats. Auditing defaults to this project directory rather than the broader sibling workspace.

## Milestone 5 — Hermes client registration (saved; native test blocked)

Only after the local stdio server is stable:

1. Save stdio configuration for the active Hermes CLI via its config command; read back the exact server entry.
2. Run `hermes mcp test html-design-advisor`; it fails inside Hermes before connecting: `module 'tools.mcp_tool' has no attribute 'StdioServerParameters'`.
3. Direct MCP Python stdio client passes initialize, tool/resource discovery, every tool call, and both resource reads.
4. Do not change the shared Hermes MCP dependency without user authorization; see ignored `MCP.local.md`.

Exit criteria (blocked): Hermes native client successfully initializes and invokes tools after the client SDK issue is resolved. No network exposure or auto-start persistence is configured.

## Deferred / separate approval

Remote crawling or search, downloading/importing templates, writing/generated code into user projects, browser-driven or deployed audits, HTTP transport, LAN exposure, authentication, and production deployment require separate threat modeling, source policy, consent boundaries, and acceptance criteria.

## Verification gates for every implementation milestone

- V0: focused tests, full suite, and build/package checks as applicable.
- V1: review schemas, caller impact, filesystem boundaries, docs, and compatibility.
- V2: independent adversarial checks against the SPEC, including negative and malformed cases.
- V3: live stdio MCP client discovers and invokes tools and reads resources; no UI/deployment claim unless those are actually tested.
- V4: resolve failures and repeat failed gates before marking the milestone complete.
