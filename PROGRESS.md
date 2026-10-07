# Progress

## 2026-10-06 — First real-site design-quality evaluation

The owner approved a local-only experiment applying the HTML Design Advisor to the Stephen Phillips homepage. The public site was inspected at https://www.stephenphillips.co.uk/ and its About and portfolio pages were used only as factual references. No production page, sibling project, or deployment was changed.

### Work completed

- Called the live stdio MCP `recommend_design` with a brief for a Devon freelance web-design/development service aimed at small businesses.
- The top three results were Daisy Days (score 5), BlockFrame (4), and Broadside (4). They are slide-deck references, not website templates; the returned caveat and unknown per-asset licensing status were preserved. Daisy Days' pastel/whimsical direction is a poor fit for the professional-services brief. This is a negative relevance result, not evidence that the recommender improved a design.
- Inspected the matching code: `_score` counts exact token overlap equally across metadata fields (name, tagline, mood, occasion, tone, best-for and scheme); all brief terms, including page-purpose terms, are tokenized without semantic purpose weighting or an `avoid_for` penalty. This explains the relevance gap and informs future ranking work.
- Created `evaluations/stephenphillips-v1/index.html`, a standalone local concept with original inline SVG, responsive CSS, semantic sections, skip link, visible focus, reduced-motion handling, and service/contact/portfolio paths. No third-party templates, fonts, scripts, or image files were copied into the project.
- Recorded the brief, returned candidates, limitations, rubric and evidence in `evaluations/stephenphillips-v1/EVALUATION.md`.
- Obtained an independent review and corrected its findings: removed an insufficiently verified client/project description and town detail, added omitted domain/SSL/content/blog/social/IT support services, and checked the entire hero at a taller desktop viewport.
- The initial concept did not use any borrowed photos, templates, fonts, or scripts.
- Updated README, CONTEXT, ROADMAP and TASKS to describe the authorized experiment and outstanding work.

### Verification

- `.venv/Scripts/python.exe -m pytest -q`: 18 passed.
- `.venv/Scripts/python.exe -m compileall -q src tests`: passed.
- `git diff --check`: passed.
- Initial MCP `audit_local_html` review: 17,239 bytes, no heuristic findings; viewport, responsive CSS, visible-focus and reduced-motion hints found. This is not a rendered audit or WCAG conformance result.
- Browser-rendered the initial local file at 1264×900 and 390×844. At 390px, document width matched the viewport; navigation fit; focus exposed the skip link. The desktop hero note and CTA fit within the hero container.

## 2026-10-07 — Feedback-driven reuse of current-site material

The owner said the first visual concept looked nice and suggested reusing authentic existing-site elements, especially imagery and testimonials. The live site remains unchanged.

### Work completed

- Added one current-site portfolio screenshot as a direct remote image reference, not a copied asset. It is labeled as a general portfolio preview rather than associated with a specific project; client/asset rights need confirmation before public redistribution.
- Added two publicly displayed reviews with their original wording, reviewer attribution and dates: Darren S. (20 June 2022) and Lead Forensics (9 November 2021). They are historical reviews and require owner confirmation before a public launch.
- Updated `README.md`, `CONTEXT.md`, `PLAN.md`, `ROADMAP.md`, `TASKS.md`, and this progress record to describe the user feedback, reused material, limitations and remaining clearance work.

### Verification

- `.venv/Scripts/python.exe -m pytest -q`: 18 passed; `.venv/Scripts/python.exe -m compileall -q src tests`: passed; `git diff --check`: passed.
- `audit_local_html` after the update reviewed 21,105 bytes and returned no heuristic findings. It detected viewport, responsive CSS, visible-focus and reduced-motion hints; it does not fetch the remote image or render the page.
- Browser checks: the portfolio image loaded at its native 150×150 size at desktop width. At 390×844, document width matched the viewport, all five navigation labels fit, review cards formed one 358px column, and internal fragment targets resolved. These checks do not establish WCAG conformance or user preference.

### Remaining

- Confirm image/client-asset rights and current testimonial/attribution status before any public release.
- Obtain owner/representative feedback on a comparative design direction before calling the prototype preferred.
- Improve recommendation relevance and negative constraints based on the slide-deck mismatch; consider the HappyMonkey.ai evaluation afterward.

All work is local. The production website was not edited or deployed; the GitHub remote was not updated.