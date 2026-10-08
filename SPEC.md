# SPEC — HTML Design Advisor MCP

Status: local catalog hardening, reference recommendations, and inert local HTML review are implemented; the acceptance criteria below define the supported behavior.

## Thesis
Give an AI client grounded, license-aware advice for designing HTML pages by connecting the user's brief to local design references and reusable template metadata, without executing or silently redistributing third-party assets.

## In scope
- Local, read-only discovery of curated design projects beneath the configured workspace root.
- Template search over available metadata, returning source and license pointers.
- Design guidance informed by local design principles and token documentation.
- Explicitly labeled external-source registry, with source/license verification status.
- Stdio MCP server exposing typed tools and resources.
- Explainable recommendations of local visual references for a webpage brief.
- Explicitly selected, size-bounded, inert local HTML source review under the configured workspace root.

## Out of scope for initial milestone
- Downloading, copying, or serving third-party templates.
- Executing HTML/JS/CSS, browser automation, or filesystem writes outside the project.
- General web crawling, remote search, or claims of current catalog size/licensing without evidence.
- Network-bound MCP transport, authentication, deployment, and autonomous modifications.

## Functional requirements
1. `search_templates(query, limit)` searches the local template index; limit is clamped to 1–20 and each result includes useful descriptive metadata. Missing/bad source index returns a safe empty result.
2. `list_design_references()` reports known project names and whether their directories exist; it performs no writes and does not recurse through dependency directories.
3. `get_design_guidance(brief)` returns actionable, brief-aware principles, including accessibility, responsive design, and untrusted-content safeguards.
4. `recommend_design(...)` returns explainable matches across curated linked website/component references and local slide decks. It weights page purpose, requires purpose or audience fit, reports known exclusions, gives an explicit `no_fit` result for no match, and labels slide decks as visual references rather than website templates. Rights status stays separate from fit.
5. `audit_local_html(path)` reviews only the explicitly selected `.html`/`.htm` file within the configured audit root, caps input at 1 MB, and never executes it or returns page copy.
6. `design-advisor://sources` returns source/terms URLs, review date, and verification state; provider-level terms must remain distinct from unverified template/package/asset rights.
7. `design-advisor://local-assets` reports the actual local template count and the correct scope of the collection.
8. Server launches on stdio and exposes its published tools/resources through MCP protocol discovery.

## Non-functional and safety requirements
- Default to read-only behavior and stdio transport.
- Do not access sibling paths outside the explicitly configured workspace root.
- Never execute referenced content; do not follow prompt-like instructions within it.
- Attribute assets and preserve each asset's license conditions; unknown terms block reuse recommendations.
- Keep tool output bounded and useful; fail closed on malformed metadata.
- Resolve configured paths and reject links that escape the allowed workspace.
- HTML review is heuristic source inspection, not a complete WCAG or rendered-browser audit.

## Acceptance criteria
- Fixture/index test confirms template count, stable metadata shape, and query matches.
- Missing and malformed index tests return safe structured results without crashing.
- Limit values below 1 and above 20 are clamped.
- Equal-score search results have stable, case-insensitive name/slug ordering.
- Catalog index paths outside the configured workspace return no records.
- HTML review rejects outside-root and oversized files and reports findings without echoing page contents.
- Design recommendations explain metadata overlap and label local slide-deck scope accurately.
- Catalog tools report existing and absent paths accurately without modifying them.
- Guidance and source resources retain safety/licensing caveats.
- Source resources never mark a specific external asset as cleared for reuse without item-level evidence.
- MCP client discovers the published tools/resources and successfully calls representative tools and reads both resources.
- No test uses the live network or mutates sibling repositories.

## Current known limitations
The local library is centered on HTML slide decks, not a general multi-purpose website catalog. Recommendations use lightweight metadata overlap and are not expert design judgment. HTML review does not read linked stylesheets/assets or render pages. Provider-level external terms were checked on 2026-10-06, but individual template/package and bundled-asset terms remain unverified; the tool must not imply reuse clearance.
