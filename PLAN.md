# Plan

## Product thesis
A local, read-only MCP advisor that helps coding agents select and adapt HTML design patterns using local references and clearly sourced external candidates.

## Is / is not
- Is: a design research and recommendation layer, source index, and later opt-in audit workflow.
- Is not: a template marketplace, a remote crawler, a website generator, or an authority to execute code or grant licenses.

## Current baseline
Current implementation exposes five tools (`search_templates`, `recommend_design`, `list_design_references`, `get_design_guidance`, `audit_local_html`) and two resources over stdio. It reads a schema-validated, configurable 34-entry local slide-template index; it also offers inert local HTML review rooted to this project by default. Provider-level terms research is recorded in `docs/research/2026-10-06-template-source-terms.md`; individual template and bundled-asset rights remain unverified. The suite contains 18 tests. A direct MCP Python stdio client discovers and exercises all tools/resources successfully. Hermes registration was saved, but its own `hermes mcp test` currently fails inside Hermes with a missing `StdioServerParameters` attribute; see ignored `MCP.local.md`. The owner-authorized first real-site evaluation is recorded in `PROGRESS.md` and `evaluations/stephenphillips-v1/EVALUATION.md`; its human-led prototype is not generated or served by the MCP.

## Phased delivery
1. Docs and acceptance contract: this spine defines boundaries and ladder.
2. Reliable local discovery: implemented and tested; see M1 in `ROADMAP.md`.
3. Provider-source terms: researched with official evidence, source licensing/status indexed, no external assets copied; specific asset rights stay unknown until an individual item is selected.
4. Local design recommendations: implemented as explainable metadata matches over visual references, with slide-deck scope and per-asset license caveats.
5. Optional page audit: implemented as inert, size-bounded HTML source inspection; no script execution or linked asset fetch.
6. Client registration: Hermes config entry saved/read back; native client smoke is blocked by a Hermes-side MCP SDK import/attribute error. Do not change Hermes dependencies until authorized.

## Pre-mortem
- Stale or inaccurate license claims could lead to improper reuse. Mitigation: per-asset provenance and unknown-by-default licensing.
- Broad filesystem crawling could leak unrelated files or hurt performance. Mitigation: curated paths, explicit root, no dependency traversal.
- Search results may overfit the slide deck library. Mitigation: label collection scope and diversify local sources.
- Untrusted template files could inject instructions or execute code. Mitigation: metadata-only indexing and no execution.
- Overly vague recommendations may be unhelpful. Mitigation: include brief constraints, evidence, and a reason for each recommendation.
