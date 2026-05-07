# Contributing

Two kinds of contribution are welcomed: **new region case studies** and **specialist improvements**.

## Adding a new region as a case study

Most valuable contribution. Demonstrates the architecture's portability and gives the next agent in your geography a head start.

1. Fork the repo.
2. Copy `specialist/reference/region/` into `case-studies/[your-market-slug]/region/`. Use lowercase, hyphen-separated (e.g., `lisbon-portugal`, `austin-tx`).
3. Fill in the six files for your market — same process described in `specialist/README.md`. The sixth file (`services.md`, new in v2) holds your vendor list — illustrative entries are fine for a case study; real entries belong in a real agent's private setup, not in a public case study.
4. Add `case-studies/[your-market-slug]/README.md` with:
   - Market name and your role (agent, broker, researcher).
   - Anything region-specific that surprised you while populating (e.g., a buyer-disclosure convention, an unusual title structure, a working-language mix).
   - Test transcripts if you ran the specialist against this region — short ones are fine. Three to five queries showing the specialist behaving correctly is plenty.
5. Open a PR.

Verification expectations: case studies should reflect real local knowledge. Don't mass-generate region files from a model — the value is in lived market expertise. If you don't yourself work the market, link to the source agent or research on which the file is based.

## Specialist improvements

Changes to anything outside `case-studies/` are improvements to the universal architecture.

Before opening a PR for a structural change:

1. Test it against at least two case studies (Jerusalem + Novato are the originals; Khao Lak is the resort/foreign-buyer counterpoint).
2. Note in the PR which case studies you tested against and what changed in the output.
3. Keep changes surgical. The architecture is intentionally lean — v2 sits at ~3,400 lines across ~22 specialist files. Additions should earn their token cost.

Particularly welcome:

- Bug fixes in the routing logic (`specialist/rules.md`) or template structures.
- New buyer-type framings in `frameworks/international-buyers.md` for buyer pools the current taxonomy under-serves.
- Improvements to intake checklists where real intake reveals gaps.
- Multi-language handling improvements (the current rules cover 1 / 2 / 3+ language markets but real-world testing will surface edge cases).

Less welcome:

- Adding new top-level files. Default is "edit, don't add."
- Long prose explanations. Bullets and tables are the house style.
- Backwards-compatibility shims when a clean change works.

## Style

- Markdown only. No build step.
- Bullets and tables over prose.
- File headers state purpose in one or two lines.
- Cross-references between files use the file path (e.g., `region/market.md`), so the LLM can locate them.

## Licensing

By contributing, you agree your contribution is licensed under the MIT License (see `LICENSE`).
