# Stephen Phillips homepage redesign — evaluation 1

Date: 2026-10-06
Status: local, non-production concept; no live-site files or settings changed.

## Test question

Can the HTML Design Advisor MCP's recommendations help produce a better-fit redesign of a real personal-services homepage, and can we catch mismatches before implementation?

## Baseline evidence

The public homepage was inspected in a browser at `https://www.stephenphillips.co.uk/` on 2026-10-06. Its first screen uses a long italic-serif headline, a green brand accent, an image carousel, and multi-link navigation. The page lists web design, development, hosting, ecommerce, SEO, CMS/blog/social media, domain names, SSL certificates, and IT support. It makes affordability and effectiveness central. The public About page describes Stephen as a self-employed freelance developer in the UK. The public portfolio page describes an A1 Positive Recycling Project redesign and launch (`https://www.stephenphillips.co.uk/portfolio/`). Those facts informed the prototype. No production edits, forms, analytics, or contact submission were attempted.

## Advisor input and observed output

Called `recommend_design` with:

- Purpose: Freelance web design and development in Devon
- Audience: Small business owners seeking web design, development, hosting and SEO
- Mood: Confident, capable, approachable, personal
- Constraints: Make services, portfolio evidence and contact options easy to find; responsive, lightweight and accessible
- Accessibility: Clear hierarchy, keyboard focus, readable contrast, mobile navigation
- Interactions: Portfolio links and contact CTA

The top results were `Daisy Days` (score 5), `BlockFrame` (4), and `Broadside` (4). The first is described as a cheerful pastel hand-drawn deck and explicitly says to avoid contexts requiring authority and precision; the second is a playful neobrutalist deck; the third is a dark dramatic editorial deck. All are labeled correctly as slide-deck visual references, and all carry an unverified per-asset license warning.

Assessment: the tool does not reliably rank for the business context. Its current scoring code counts exact token overlap equally across metadata fields (name, tagline, mood, occasion, tone, best-for and scheme); it tokenizes all brief fields, including page purpose, without semantic page-purpose/category weighting or an `avoid_for` penalty. The first result is a poor website recommendation. This is a useful negative test: do not use the current rank order as design direction. The design below uses the site's green/local identity and the real service list as context, with independent project-specific choices for layout and visual language.

## Prototype

Open `index.html` locally. It is a static document; the hero illustration is original inline SVG, with no third-party templates, fonts, or scripts. Following owner feedback, it now hotlinks one 150×150 portfolio screenshot from the existing site rather than copying it into this repository; that image needs an internet connection and its rights should be reconfirmed before public redistribution. It also shows two attributed public reviews with their original dates. The page is not connected to production APIs or forms. Contact actions are email links; the portfolio summary should be checked against the full case study before publication.

Direction: an editorial, grounded Devon identity—limestone paper, deep green, a restrained copper accent, a custom coast/hills illustration, and clear service rows rather than a generic card grid. The page makes the offer and the next action visible, then sequences services, selected work, process, and contact.

## Reusing current-site proof points

On 2026-10-07, the owner said the first visual concept looked nice and suggested retaining authentic material from the current site, including images and testimonials. In response, the work section now includes a thumbnail hotlinked from the public homepage gallery: `https://www.stephenphillips.co.uk/wp-content/uploads/2022/02/Screenshot-2022-02-02-155303-150x150.png`. It visually shows a seaside-themed website screenshot and is presented only as a general portfolio preview, not attributed to A1 Positive Recycling Project. Its source is not copied or modified; image ownership/client permissions were not independently established, so keep this as a private preview until cleared.

The reviews section reproduces two reviews publicly displayed on the homepage, preserving their wording, reviewer attribution, and date: Darren S. (20 June 2022) and Lead Forensics (9 November 2021). Source: `https://www.stephenphillips.co.uk/`. These are historical testimonials; confirm their current status and any attribution requirements before a public launch.

## Evaluation rubric (heuristic, 1 = weak, 5 = strong)

The scores are the designer's first-pass judgments, not independently validated results. The independent review identified potential factual overreach and missing service coverage; those were corrected in the prototype before these notes were finalized. Owner verification and user research remain outstanding.

| Dimension | Score | Evidence / caveat |
|---|---:|---|
| Audience and service clarity | 4 | Hero says who/what; all five service groupings are explicit. Copy and pricing need owner review. |
| Primary action and navigation | 4 | Email CTA, work link, and section navigation are visible; no submission flow exists. |
| Use of real site context | 4 | Retains Devon/local and service identity; includes services and one project described on the public portfolio page. Confirm exact wording and offerings with the owner. |
| Visual specificity | 4 | Local landscape illustration, restrained green/copper palette, editorial hierarchy; still a first-pass concept, not a tested brand system. |
| Responsive / keyboard foundations | 4 | At 390px, body width stayed 390px, all nav labels fit, skip link appeared on focus, and layout collapsed to one column. Needs broader device and assistive-tech testing. |
| MCP recommendation usefulness | 2 | Accurate scope/licensing caveats, but top-ranked references do not fit well. Requires better negative constraints and relevance ranking. |
| Accessibility confidence | 2 | Semantic landmarks, focus rule, skip link, reduced-motion and viewport/responsive rules present. The MCP audit is only heuristic and is not WCAG conformance evidence. |

Scores are design-review judgments, not user research or an automated benchmark.

## Verification performed

- Direct MCP call to `recommend_design`: returned the three references above, with the slide-deck caveat and per-asset license warnings.
- Direct MCP call to `audit_local_html` after adding reused page material: `status=reviewed`, 21,105 bytes, no heuristic findings; viewport, responsive CSS, focus and reduced-motion signals found. This tool does not execute/render the page or fetch the remote image and is not a full WCAG audit.
- Independent review: flagged potential town/client overreach, omitted service categories, unsupported explanation for the scoring issue, and an initial viewport screenshot that cut off the hero's lower edge. Removed the unverified second client/project description, retained only Devon, added domains/SSL/content/social/IT support, and checked the scoring code directly. A 1264×900 render shows the note and CTA fully inside the hero; DOM bounds confirm the note stays within its container.
- Browser checks after the reuse update: at desktop width the exact source image loaded at 150×150 with descriptive alt text; at mobile 390×844 the document width matched the viewport, review cards switched to one 358px column, all navigation items fit, and internal fragment targets resolved. No production site was changed.

## Next experiment

This is one human-led local concept informed by an actual MCP call; it is not a page generated by the MCP, nor proof that the current recommender improved the design. For a stronger comparison, produce a second, explicitly recommendation-led variant or first improve recommendation ranking, then ask the site owner or representative small-business visitors to compare both on clarity, trust, distinctiveness, and contact intent. Repeat for `happymonkey.ai` only after reviewing this evaluation.