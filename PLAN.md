# Plan

## Product thesis
A local, read-only MCP advisor that helps coding agents select and adapt HTML design patterns using local references and clearly sourced external candidates.

## Is / is not
- Is: a design research and recommendation layer, source index, and later opt-in audit workflow.
- Is not: a template marketplace, a remote crawler, a website generator, or an authority to execute code or grant licenses.

## Original baseline
Current implementation exposes five tools (`search_templates`, `recommend_design`, `list_design_references`, `get_design_guidance`, `audit_local_html`) and two resources over stdio. It reads a schema-validated, configurable local slide-template index when available; it also offers inert local HTML review rooted to this project by default. Provider-level terms research is recorded in `docs/research/2026-10-06-template-source-terms.md`; individual template and bundled-asset rights remain unverified. The suite contains 26 tests. A direct MCP Python stdio client discovers and exercises all tools/resources successfully. Two owner-authorized real-site evaluations and one fictional editorial example are recorded under `evaluations/`. The real-site concepts were manually authored and are neither generated nor served by the MCP.

2026-10-08 update: `recommend_design` now also ranks five linked W3.CSS website layouts and one ThreeUI Community component reference, with purpose/constraint weighting, known-conflict exclusion and honest no-fit behavior. The source review and current before/after comparison are under `docs/research/2026-10-08-*.md`. The suite now has 26 passing tests, and live stdio discovery, five calls and two resource reads pass. Bundled image/media rights and owner visual preference remain unverified.

## Phased delivery
1. Docs and acceptance contract: this spine defines boundaries and ladder.
2. Reliable local discovery: implemented and tested; see M1 in `ROADMAP.md`.
3. Provider-source terms: researched with official evidence, source licensing/status indexed, no external assets copied; specific asset rights stay unknown until an individual item is selected.
4. Local design recommendations: implemented as explainable metadata matches over visual references, with slide-deck scope and per-asset license caveats.
5. Optional page audit: implemented as inert, size-bounded HTML source inspection; no script execution or linked asset fetch.
6. Stdio client protocol smoke has been verified directly; client-specific setup is outside the project release contract.

## Next improvement cycle — website relevance

Goal: make `recommend_design` useful for webpage briefs while retaining the read-only stdio server and explicit provenance. The September 2026 bookmark export is a lead list, not license or quality evidence.

1. **Freeze a baseline.** Turn the Stephen Phillips and HappyMonkey briefs into a small evaluation set, alongside portfolio, editorial, minimal, and conflicting-constraint cases. Record current recommendations, reasons, `avoid_for` conflicts, and whether a website-specific reference is available. Judge relevance separately from license status.
2. **Fix ranking before expanding the catalog.** Give page purpose and explicit constraints more weight than mood-word overlap. Treat `avoid_for` conflicts as exclusions or clearly explained penalties. Return a genuine no-fit result when the library has no suitable candidate, instead of promoting an arbitrary slide deck. Keep scores and reasons deterministic and bounded.
3. **Research a small website-reference set.** Review the bookmarked Rewamp UI, ThreeUI, and design-resource roundup as candidate leads, plus existing local website-oriented sources. For each selected item, record canonical URL, reference type, intended use, evidence date, license pointer, attribution requirements, asset-rights status, and limitations. Use metadata and links only; do not download, execute, copy, or recommend reuse of uncleared assets. Admit only a small, varied set that improves the evaluation briefs.
4. **Improve the recommendation response.** Show website references and slide-deck visual references as distinct types. Give concise palette, type, layout, and interaction cues grounded in the selected metadata, with explicit conflicts and unknown rights. Keep the existing tool name and input contract if possible; document any output changes for MCP clients.
5. **Check quality and protocol behavior.** Compare before/after outputs against the evaluation set and review false positives independently. Run focused and full Python tests, `git diff --check`, boundary and hostile-metadata cases, and a live stdio MCP client discovery/call/resource read. Seek owner or representative preference feedback before claiming that a visual direction is preferred.

Initial success criteria: neither real-site brief receives an `avoid_for` conflict as an unexplained top recommendation; explicit constraints affect ordering or produce no-fit; website references have item-level provenance fields and honest license status; existing search, audit, resources, and filesystem boundaries continue to work.

## Pre-mortem
- Stale or inaccurate license claims could lead to improper reuse. Mitigation: per-asset provenance and unknown-by-default licensing.
- Broad filesystem crawling could leak unrelated files or hurt performance. Mitigation: curated paths, explicit root, no dependency traversal.
- Search results may overfit the slide deck library. Mitigation: label collection scope and diversify local sources.
- Untrusted template files could inject instructions or execute code. Mitigation: metadata-only indexing and no execution.
- Overly vague recommendations may be unhelpful. Mitigation: include brief constraints, evidence, and a reason for each recommendation.
