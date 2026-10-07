# HappyMonkey.AI — local design-advisor evaluation 2

Date: 2026-10-07
Status: local experiment only; neither deployed nor an approved replacement

## Test question

Does the HTML Design Advisor help shape a second, materially different site—a software-first engineering portfolio with projects, open-source work, writing and contact—rather than the first freelancer-services homepage?

## Source basis

The public homepage presents HappyMonkey.AI as software and AI engineering work, with projects, open-source tools, About and writing content, and a contact route. Its visible page contains nine project entries and six open-source tools.[1] The implementation preserved distinctions between products, experiments, open-source tools and writing; it does not claim every project is commercial or AI-powered.

I inspected the live page in BrowserOS Neo and used it as factual reference only. The source citation is the public homepage. No live page, production asset or sibling project was modified.

## Actual advisor output

The actual MCP `recommend_design` call returned:

| Rank | Reference | Score | Assessment for this brief |
|---|---|---:|---|
| 1 (tie) | Daisy Days | 7 | Pastel/hand-drawn slide deck. Its own `avoid_for` warns against contexts expecting authority and precision. Poor structural fit. |
| 1 (tie) | Studio | 7 | Dark deck with electric-yellow type. Its high-contrast palette was a usable visual seed, but the reference is still a loud agency/brand presentation, not a portfolio website. |
| 3 | Capsule | 6 | Warm, pastel, pill-card slide deck; its `avoid_for` also warns against institutional weight. Weak fit. |

The MCP correctly labeled all three as HTML slide-deck visual references, not ready-to-use website templates, and preserved the unverified per-asset license caveat. No catalog assets were copied or used.

The design-guidance tool returned relevant baseline principles—ground choices in audience and page purpose, avoid generic chrome, use readable line lengths, visible focus, responsive semantics and contrast—but did not supply a page-specific layout. In the current scorer, exact brief-token overlap is counted across metadata fields, while `avoid_for` is returned but not used as a negative score. Daisy Days therefore tied for first despite its own authority/precision warning. The same slide-deck bias appeared in the first evaluation; this second case confirms a relevance limitation, not evidence that the recommender generated or improved the page.

## Human-authored concept

Created `index.html` as a standalone static concept. The visual direction is an editorial engineering workbench: navy surfaces, lime/cyan accents, serif display type, a small original CSS workflow diagram, aligned project rows, and separate sections for open source, About, writing and contact. The hero keeps the existing “Software first. AI where it helps.” proposition.[1]

The page was authored manually after reviewing the advisor results. It does not use a third-party template, external image, remote font, stylesheet or script. External links point to the public project destinations presented by the source site.[1] No form is submitted; contact uses a mail link. This is a human-made experiment informed by MCP advice, not an MCP-generated webpage. The longer hero principle and custom section headlines are proposed copy, not verbatim quotations, testimonials or independently verified project claims.

## First-pass rubric (author assessment, not user testing)

| Measure | Score | Reason |
|---|---:|---|
| Audience and purpose clarity | 4/5 | Software-first positioning is explicit and the engineering workflow is visible. |
| Hierarchy and calls to action | 4/5 | Work and contact are distinct next steps; the primary and secondary actions are grouped. |
| Factual fit | 4/5 | The page separates project types and avoids invented commercial-status claims; source content is summarized, not exhaustively reproduced. |
| Visual specificity | 4/5 | A distinct editorial palette and original workbench illustration replace generic template cards. |
| Responsive/keyboard foundations | 4/5 | Semantic sections, skip link, visible focus, responsive grids and reduced-motion handling; not a full accessibility audit. |
| Advisor relevance | 2/5 | One palette reference was mildly useful; the top three were slide decks and gave no suitable site structure. |

These ratings are a structured self-review, not owner preference evidence or a claim of WCAG conformance.

## Verification

- `audit_local_html` reviewed 22,891 bytes and returned no heuristic findings. It detected viewport metadata, responsive CSS, visible-focus/reduced-motion hints and `header`, `nav`, `main` and `footer` landmarks. The tool does not render or execute the page and is not a complete WCAG audit.
- BrowserOS Neo rendered the local file at 1280×900 and captured a desktop screenshot. The hero heading stayed on two clean lines; both actions remained together. The Projects navigation link changed the fragment to `#projects` and settled with its section heading in view.
- At 390×844, BrowserOS DOM checks found document width equal to viewport width (390px), no missing internal anchors, the navigation and project content within the viewport, nine project entries and six tools. The project title/description columns aligned; tool and writing grids collapsed to one column; the two hero actions wrapped cleanly. Mobile verification is DOM/layout evidence, not a captured mobile screenshot.
- Focusing “Skip to content” exposed it at the top of the viewport; its target is the main content landmark.
- Calculated text contrast for representative CSS pairs: ink on night 17.21:1, muted on night 11.61:1, muted on panel 10.50:1, lime on night 15.50:1, and dark contact text on lime 11.40:1. These are selected color-token checks, not an exhaustive contrast audit.
- The local `google/gemma-4-e2b` visual review judged the hierarchy and CTAs clear; it suggested slightly more vertical breathing room. That remains a subjective refinement suggestion, not a functional issue.

## Result and limits

The page demonstrates that a coherent second concept can be authored from the public site's actual content, but the MCP did not produce the concept. Its general guidance helped frame accessibility requirements; its top-ranked references were again only weakly relevant because the catalog is slide-deck-centered. Improving purpose-aware ranking and negative-constraint handling remains the useful product follow-up.

This prototype remains local, is not a production recommendation, and has not been approved through comparative owner/user preference testing.

## Sources

[1] https://happymonkey.ai — HappyMonkey.AI homepage
