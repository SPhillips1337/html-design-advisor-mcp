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
- Fixed an owner-reported contrast problem: the site-wide `footer` rule had unintentionally given each review byline a dark-green background while leaving its date muted. Scoped the dark treatment to `.site-footer`, then set review dates to 16px, bold, dark ink, stacked and left-aligned beneath names.
- Unified the work rows' copy column so A1's description stays with its heading; the unrelated thumbnail is a distinct general portfolio preview.
- Updated `README.md`, `CONTEXT.md`, `PLAN.md`, `ROADMAP.md`, `TASKS.md`, and this progress record to describe the user feedback, reused material, limitations and remaining clearance work.

### Verification

- `.venv/Scripts/python.exe -m pytest -q`: 18 passed; `.venv/Scripts/python.exe -m compileall -q src tests`: passed; `git diff --check`: passed.
- `audit_local_html` after the image/reviews and readability/layout refinements reviewed 21,166 bytes and returned no heuristic findings. It detected viewport, responsive CSS, visible-focus and reduced-motion hints; it does not fetch the remote image or render the page.
- BrowserOS Neo checks after the correction: desktop title and description x-positions matched in both work rows; mobile 390×844 document width stayed 390px, navigation stayed within the viewport, reviewer dates appeared at 16px and left-aligned, and the review grid used one 358px column. The image preview and A1 entry are separate.
- Calculated date contrast improved from 2.33:1 (`#52635b` on unintended `#182b25`) to 12.00:1 (`#182b25` on `#e9e7dc`). Local `google/gemma-4-e2b` vision review judged the updated mobile dates readable and the work preview clearly separate. These checks are not a full WCAG audit or user-preference test.

### Remaining

- Confirm image/client-asset rights and current testimonial/attribution status before any public release.
- Obtain owner/representative feedback on a comparative design direction before calling the prototype preferred.
- Improve recommendation relevance and negative constraints using both evaluations; see the HappyMonkey.AI results below.

The Stephen concept remains non-production; its public source website was not edited or deployed. Its hotlinked image and historical reviews still require clearance before any public release.

## 2026-10-07 — Second real-site design-quality evaluation: HappyMonkey.AI

The owner asked for a second test to see whether the HTML Design Advisor could help with a different site. The official homepage was reviewed as a factual reference; evidence, citations, advisor output and limitations are in `evaluations/happymonkey-v1/EVALUATION.md`. The live site was not changed.

### Work completed

- Called the actual MCP `recommend_design` with a software-first engineering portfolio brief and called `get_design_guidance` for the same case.
- The top recommendations were Daisy Days (7), Studio (7) and Capsule (6). All were slide-deck visual references rather than website templates. Daisy Days tied for first despite its own `avoid_for` warning about contexts needing authority and precision; the current token-overlap scorer does not use that negative field to lower the score.
- Manually authored `evaluations/happymonkey-v1/index.html`, a static concept that separates projects, open-source tools, About, writing and contact. It uses no copied third-party image, template, remote font or script. It is not generated or served by the MCP.
- Documented the actual results, rubric, source citation, limitations and follow-up in `evaluations/happymonkey-v1/EVALUATION.md` and updated README, CONTEXT, PLAN, ROADMAP and TASKS.

### Verification

- `audit_local_html`: 22,891 bytes read; no heuristic findings; viewport, responsive CSS, visible focus, reduced-motion and semantic-landmark signals found. This is not a rendered audit or WCAG conformance result.
- BrowserOS Neo rendered the final local page at 1280×900 and captured a desktop screenshot. It verified a two-line headline, grouped actions and a successful Projects anchor navigation.
- At 390×844, DOM checks found `scrollWidth == clientWidth == 390`; no missing internal anchors; nine projects and six tools; project titles/descriptions aligned; tools and writing became single-column; hero actions wrapped within the viewport. Mobile evidence is from DOM/layout inspection, not a mobile screenshot.
- The skip link became visible at the top of the viewport when focused. Selected text-pair contrast calculations ranged from 10.50:1 to 17.21:1; these do not cover every text/background state.
- The local `google/gemma-4-e2b` screenshot review found the hierarchy and CTAs clear and suggested a little more vertical breathing room. That remains a subjective refinement note.
- Citation verification for `EVALUATION.md` passed; the public homepage is its numbered source.
- `.venv/Scripts/python.exe -m pytest -q`: 18 passed; `.venv/Scripts/python.exe -m compileall -q src tests` and `git diff --check` passed.

### Result and remaining

The second case confirms a repeated limitation: the advisor's slide-deck-centered references do not give reliable website structure or purpose-aware ranking. General guidance was useful as a checklist; the prototype itself was human-authored. M6 remains in progress pending comparative owner/participant preference feedback and recommendation-ranking improvements. Both concepts remain unapproved, non-production prototypes. Their source websites were not edited or deployed; the evaluation is stored in the existing private GitHub repository.