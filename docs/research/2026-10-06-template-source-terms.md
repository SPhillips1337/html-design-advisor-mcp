# Template-source terms review — 2026-10-06

Scope: checked official source and terms pages for candidate catalogs to support discovery/advisory only. This is not legal advice. A source-level policy does not establish the license of every template, image, icon, font, or bundled library. Verify the downloaded template package and asset attribution before using it in a product. No third-party templates or assets were downloaded.

## Findings

### html.design
- Catalog: https://html.design/
- Official license: https://html.design/license/
- The license page, marked “LAST UPDATED: APR 23, 2026,” says templates are CC BY 3.0, permits personal and commercial use, modification, and distribution, and requires visible credit. It states a README/about mention can replace a footer credit after 50%+ of markup/CSS has changed. It also prohibits claiming original authorship and re-selling templates as-is on marketplaces.
- The same page warns that included placeholder images can carry separate licenses. Check each image and other third-party asset; replace when uncertain.
- Status: official license page read; use only with required attribution and per-asset review.

### Colorlib
- Catalog: https://colorlib.com/wp/templates/
- Official license: https://colorlib.com/wp/licence/
- The license page describes paid templates as licensed for the buyer's and clients' websites, with modification and credit removal; its license prohibits reselling/sharing a template or modified template as a template/theme/starter kit, and disallows publishing template source files for download. Bundled libraries/fonts/icons keep their own licenses; demo photos are preview-only and should be replaced.
- The same page separately says free code snippets and other free resources are CC BY 3.0, require the credit link, and cannot be resold as template/theme/snippet packs. Do not generalize this snippet license to the separately sold website templates or assume every catalog listing has identical terms.
- Status: official license page read; template-specific package/license required.

### TemplateMo
- Catalog: https://templatemo.com/
- Official usage page: https://templatemo.com/about
- Official FAQ: https://templatemo.com/contact
- About page says templates may be downloaded, modified, and customized for client work; the user may charge for their service and remove credit while editing. The contact FAQ explicitly says redistributing templates on another website is not allowed.
- The site describes broad usage permission but does not identify a standard open-source license such as MIT or CC BY on the cited pages. Do not redistribute the templates themselves; inspect a specific package for additional terms.
- Status: source usage/redistribution pages read; no blanket OSI/Creative Commons license claim.

### uiCookies
- Catalog: https://uicookies.com/
- General terms page: https://uicookies.com/license/
- The official license page search-result text says free templates are CC BY 3.0 “and some additional attributions”; it permits personal/business use and modification but says footer copyright credit may not be removed and free templates may not be redistributed/resold/rented/leased. Paid license options can remove attribution.
- The license page's current title/snippet and descriptions on individual pages may not align perfectly; treat attribution as template-specific and verify the current individual template page and package. No broad no-attribution or unrestricted redistribution claim is safe.
- Status: official license page located; exact asset terms require checking the individual listing/package.

### W3Schools W3.CSS templates
- Gallery: https://www.w3schools.com/w3css/w3css_templates.asp
- The gallery says its responsive W3.CSS website templates may be modified, saved, shared, and used in projects. This permission applies to those listed templates; it is not a blanket license for unrelated W3Schools content or third-party assets in a template.
- Status: gallery page read; check asset-level terms for images/fonts/icons and do not call all W3Schools content open source.

### GitHub: dawidolko/Website-Templates
- Repository: https://github.com/dawidolko/Website-Templates
- License file: https://github.com/dawidolko/Website-Templates/blob/master/LICENSE
- GitHub repository listing identifies an MIT license and describes a collection of 170 HTML5 website templates. A repository-level MIT license is not enough to establish that every imported template or bundled asset was authored by the repository owner or can be relicensed; review each folder, upstream origin, and asset license before using it.
- Status: official license file read at the raw GitHub URL; root repository license is MIT, but per-template and bundled-asset rights remain unverified.

### GitHub: beautiful-html-templates (already local)
- Repository: https://github.com/zarazhangrui/beautiful-html-templates
- Local checkout: `../beautiful-html-templates/`
- The local checkout includes `LICENSE` (MIT) and `index.json` (34 template records). Its README describes the library as HTML slide templates, not a general website template catalog. Preserve the MIT copyright/license notice and check each template's provenance/assets before reuse.
- Status: local root license and index read; 34 indexed examples; slide-deck-specific.

## Source registry integration policy

- `terms_page_checked` means only that the cited provider terms were checked; it does not mean a specific asset is cleared for a use.
- Keep `asset_license_status` unverified unless the individual template/package and bundled assets are inspected.
- Recommendations may mention visual references separately from reuse permissions. Unknown or incompatible asset terms must never become “safe to reuse.”
- Counts (800+, 1,500+, 620+, 188) were user-provided or provider marketing claims; this review did not independently count catalogs. Do not expose those figures as verified counts.

## Verification sources

All provider evidence URLs above are official provider or repository pages, accessed 2026-10-06. html.design license, Colorlib license, TemplateMo about/contact, and W3.CSS gallery text was read from those pages in a browser. The dawidolko MIT license file was directly read from GitHub raw content. uiCookies details were confirmed from official-page search-result text; re-open the license page/package before relying on any template-specific term. Counts (800+, 1,500+, 620+, 188, and 170) are not independently counted and should be treated as provider/repository marketing or index statements, not verified inventory totals.
