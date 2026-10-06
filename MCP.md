# MCP intent map

Transport: stdio. Server runs locally from this project; it does not bind a network port.

Tools:
- `search_templates`: search indexed local template metadata and return descriptive fields and license pointer.
- `recommend_design`: map page purpose, audience, mood, and constraints to local visual references with match evidence and caveats.
- `list_design_references`: summarize curated local design projects without recursive dependency traversal.
- `get_design_guidance`: return accessibility-aware principles and links to workspace design guidance.
- `audit_local_html`: review one explicitly selected local HTML file as inert text; allowed root and size are enforced.

Resources:
- `design-advisor://sources`: candidate source registry with verification states.
- `design-advisor://local-assets`: actual local template count, source, and collection scope.

No credentials or remote integrations are needed. Any later web-fetch capability requires an explicit domain allowlist, provenance records, and tests against untrusted instructions.
