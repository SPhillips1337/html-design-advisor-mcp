# Recommendation relevance baseline

Checked 2026-10-08. Inputs use the documented Stephen Phillips evaluation brief and a HappyMonkey.AI software-engineering portfolio brief. Scores are internal token scores, not a design-quality measurement.

| Brief | Before change | After change | Review |
|---|---|---|---|
| Stephen Phillips freelance-services homepage | Daisy Days 4; BlockFrame 3; Broadside 3 | W3.CSS Architect 4; W3.CSS Startup 4; Retro Zine 2 | The top two are website layouts with services/projects/contact structure. Daisy Days is excluded by its authority/precision warning. Retro Zine remains a lower-ranked visual seed, not a website structure. |
| HappyMonkey.AI software-engineering portfolio | Coral 4; Neo-Grid Bold 4; BlockFrame 3 | W3.CSS Startup 10; W3.CSS Architect 9; W3.CSS Dark Portfolio 9 | All three results are whole-page examples. Startup has offer/work/contact structure; Dark Portfolio needs adaptation away from photo-heavy proof. These are structural references, not endorsements of demo copy, imagery or visual quality. |

Additional current-code checks:

| Brief | Current top result | Assessment |
|---|---|---|
| Personal software portfolio | W3.CSS Dark Portfolio 14; Architect 10; Startup 10 | Whole-page personal/work structure; photo-heavy proof and demo pricing need adaptation. |
| Editorial writing/research publication | W3.CSS Blog 14; Broadside 8; Cartesian 8 | Dated article hierarchy and navigation fit better than a slide deck; demo copy and imagery have no reuse clearance. |
| Minimal lightweight personal page | W3.CSS Start Page 15; Dark Portfolio 6; Pink Script 4 | Sparse introduction and one action fit the brief; lower-ranked examples need more adaptation. |
| Unrelated `nonsense-zxq` purpose | `no_fit` | No candidate is promoted without a purpose or audience match. |
| Business brief with only an authority-conflicting candidate | `no_fit`, with excluded reason | The conflict is visible in `excluded_references`. |

The live current-code Stephen and HappyMonkey results also include `excluded_references` for Daisy Days and other slide references whose own `avoid_for` descriptions warn about authority or precision. The website entries carry direct item URLs and separate provider-license and bundled-asset verification fields. A website lead also supplies a `recommended_direction` with grounded layout, palette, type and interaction cues; no direction is invented for no-fit or slide-only output.

The earlier `evaluations/*/EVALUATION.md` files used their own dated briefs and observed scores; this note records a reproducible current-code comparison and does not rewrite those historical results. Source rights and relevance are separate judgments. Asked on 2026-10-08 whether the HappyMonkey.AI evaluation should favor the editorial engineering workbench or a conventional startup layout; the owner expressed no preference yet. No visual direction is designated preferred.
