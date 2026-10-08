# Development roadmap

Product goal: a local, read-only MCP advisor that helps an AI client choose and review HTML page designs using the user's brief, local design references, and source/license evidence.

Status: M0, M1, M2 provider-source research, M3 relevance follow-up, and M4 are implemented and verified. M3 now has five curated linked website layouts and one interactive component reference alongside local slide decks; bundled asset rights remain unverified. Direct stdio MCP discovery and tool/resource calls passed. Roadmap items do not authorize template downloads, project writes, or deployment.

Owner-authorized evaluation status: M6 now has local-only Stephen Phillips and HappyMonkey.AI homepage concepts. Both cases exposed weak website relevance in the original slide-deck-centered recommender; the dated evaluations retain that historical result. The 2026-10-08 relevance follow-up improves ranking and records current outputs in `docs/research/2026-10-08-recommendation-baseline.md`. The concepts passed the MCP's heuristic source review; browser checks are documented per evaluation. Neither is approved as a replacement, and neither public site was changed.

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

## Milestone 5 — MCP client protocol smoke (complete)

A direct MCP stdio client initialized the server, discovered all five tools and two resources, called every tool, and read both resources. Client-specific configuration is left to the user and their MCP host documentation.

## Milestone 6 — Real-site design quality evaluation (in progress)

Goal: test whether advisor outputs improve a real site's proposed redesign, and distinguish useful guidance from superficial keyword matches.

1. Inspect one public page and derive a brief from observed content; do not infer private requirements.
2. Call the actual MCP recommender and record candidate fit, scope labels, and license caveats.
3. Build a local-only prototype, prioritizing owner-provided/current-site material; use external assets only when rights are clear. No deployment, production edits, or sibling-project changes. The Stephen thumbnail is a provisional hotlink, not cleared for public reuse; the HappyMonkey concept uses no external assets.
4. Evaluate using a rubric for audience/service clarity, hierarchy/CTA, factual fit, visual specificity, responsive/keyboard foundations, and advice relevance.
5. Check source heuristics with `audit_local_html`, then render at desktop/mobile widths; state that neither proves WCAG conformance or user preference.
6. Use owner/representative feedback before claiming a preferred direction; compare both cases and improve advisor ranking or retain an explicit limitation before choosing further evaluation targets.

Current evidence: `evaluations/stephenphillips-v1/EVALUATION.md`, `evaluations/happymonkey-v1/EVALUATION.md`, and `PROGRESS.md` record both runs. For HappyMonkey, all three returned recommendations were slide decks (scores 7/7/6); Daisy Days tied for first despite its own `avoid_for` warning about authority/precision. The manually authored local concept rendered at 1280×900; at 390×844 the DOM checks found no horizontal overflow, missing anchors, or project-column misalignment. Its source audit returned no heuristic findings, and a local vision review found the hierarchy/CTAs clear. The results are not user-preference evidence; comparative owner/participant review and recommendation-ranking improvements remain pending.

Exit criteria: documented recommendation-vs-context assessment, rendered responsive prototype, explicit owner/participant review, and follow-up tuning or a clear decision not to use the advisor for that case. A local prototype is not a production release.

## Deferred / separate approval

Remote crawling or search, downloading/importing templates, writing/generated code into user projects, browser-driven or deployed audits, HTTP transport, LAN exposure, authentication, and production deployment require separate threat modeling, source policy, consent boundaries, and acceptance criteria.

## Verification gates for every implementation milestone

- V0: focused tests, full suite, and build/package checks as applicable.
- V1: review schemas, caller impact, filesystem boundaries, docs, and compatibility.
- V2: independent adversarial checks against the SPEC, including negative and malformed cases.
- V3: live stdio MCP client discovers and invokes tools and reads resources; no UI/deployment claim unless those are actually tested.
- V4: resolve failures and repeat failed gates before marking the milestone complete.
