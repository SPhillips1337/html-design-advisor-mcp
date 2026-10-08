# MCP intent map

Transport: stdio. Server runs locally from this project; it does not bind a network port.

Tools:
- `search_templates`: search indexed local template metadata and return descriptive fields and license pointer.
- `recommend_design`: map page purpose, audience, mood, constraints, accessibility needs, and interactions to curated linked website/component references and local slide-deck visual references. A purpose or audience fit is required for a match. The response includes evidence, provenance, caveats, `matched`/`no_fit` status, up to five `excluded_references` with reasons, and `recommended_direction` cues when the lead reference has documented cues. No remote content is fetched.
- `list_design_references`: summarize curated local design projects without recursive dependency traversal.
- `get_design_guidance`: return accessibility-aware principles and links to workspace design guidance.
- `audit_local_html`: review one explicitly selected local HTML file as inert text; allowed root and size are enforced.

Resources:
- `design-advisor://sources`: candidate source registry and curated website-reference metadata with verification states.
- `design-advisor://local-assets`: actual local slide-template count, curated website/component reference counts, source, and collection scope.

No credentials or remote integrations are needed. Any later web-fetch capability requires an explicit domain allowlist, provenance records, and tests against untrusted instructions.
