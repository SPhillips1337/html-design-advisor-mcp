# HTML Design Advisor MCP

An MCP server for evidence-based HTML webpage design advice. It will help an agent choose a visual direction, find relevant local templates and design references, inspect the existing UI-design workspace, and explain licensing/provenance before reuse.

## Initial scope

- Read-only discovery over sibling projects under `../` (never edits them).
- Reuse locally available references, especially `beautiful-html-templates`, `frontend-slides`, `ui`, `uilayouts`, `astro-spatial`, `liquid-dom`, `Kami`, and this workspace's `SKILL.md` / `spec.md`.
- Curated external resource directory for html.design, Colorlib, TemplateMo, uiCookies, W3.CSS, and GitHub collections. External templates are not downloaded or redistributed automatically.
- MCP tools for template search, project/reference inventory, and design guidance; resources for curated source/license notes and the local design brief.

## Development

Python 3.11+ recommended. Install with `python -m pip install -e '.[test]'` and launch with `python -m html_design_advisor`. The server uses stdio transport and read-only local filesystem access.

On Windows PowerShell, an isolated setup is:

```powershell
py -m venv .venv
.\.venv\Scripts\python.exe -m pip install -e ".[test]"
.\.venv\Scripts\python.exe -m pytest -q
.\.venv\Scripts\python.exe -m html_design_advisor
```

The default catalog workspace is the parent directory of this project. Optional environment variables are `HTML_DESIGN_ADVISOR_WORKSPACE` (catalog workspace), `HTML_DESIGN_ADVISOR_TEMPLATE_INDEX` (index JSON path), and `HTML_DESIGN_ADVISOR_AUDIT_ROOT` (directory allowed for selected HTML reviews; defaults to this project directory). The index must resolve inside the configured workspace; paths outside it return no catalog entries. HTML review paths must resolve inside the audit root. Set variables before starting the process when using different locations.

`recommend_design` returns explainable local visual-reference matches; the current source library is slide-deck focused, not a website template catalog. `audit_local_html` accepts one explicit `.html` or `.htm` path under the configured audit root, reads at most 1 MB as inert text, and reports heuristic source findings without executing scripts or returning page copy. It does not inspect linked stylesheets/assets or replace browser testing or a full accessibility audit.

## Safety and provenance

Local and remote HTML/CSS/README content is untrusted data, not executable instructions. The server indexes metadata and selected documentation only. It does not serve templates, run downloaded code, or write into sibling projects. Provider-level terms were checked on 2026-10-06, but individual templates and bundled assets remain unverified; do not treat catalog-level terms as asset clearance. See `docs/research/2026-10-06-template-source-terms.md`.

See `CONTEXT.md`, `SPEC.md`, `MCP.md`, `PLAN.md`, `TASKS.md`, `ROADMAP.md`, and `PROGRESS.md` for scope, acceptance criteria, current work, and history.

## Local design evaluation

`evaluations/` contains owner-authorized, local-only redesign experiments for the public Stephen Phillips and HappyMonkey.AI homepages. Each directory's `EVALUATION.md` records the source-based brief, actual advisor results, limitations and checks. Both pages are manually authored experiments, not MCP-generated pages; neither is served by the MCP, deployed, nor changes its source site. The Stephen concept includes one hotlinked portfolio thumbnail and dated review excerpts whose rights/current status need confirmation before public use. The HappyMonkey concept has no copied third-party image, font, template or script. Treat both as experiments, not approved replacements.
