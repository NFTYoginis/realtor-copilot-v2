# Case Study — Khao Lak Region Pack (POPULATED)

This folder contains a populated Khao Lak (Phang Nga, Thailand) region pack. To use the specialist for Khao Lak:

1. Copy the contents of this folder over `realtor-copilot/specialist/reference/region/`.
2. Drop the `specialist/` folder into your Claude Project.

Files in this pack:

- `market.md` — Khao Lak buyer segments (Northern European retirees, Russian and growing Chinese investors, Thai locals), seasonality (Nov–Apr high season; tsunami-anniversary date sensitivity), foreign-buyer activity, pricing adjustment magnitudes in THB, buyer-disclosure conventions (tsunami zone, monsoon flood history, lease registration, foreign-quota status, STR restrictions)
- `regulations.md` — Thai transfer fee, Specific Business Tax, Stamp Duty, Withholding Tax; Land and Building Tax (post-2020); title hierarchy (Chanote → Sor Kor 1); foreign-ownership rules (49% condo quota, leasehold + freehold-structure, FET / Foreign Exchange Transaction form, POA for remote close)
- `neighborhoods.md` — Khao Lak sub-areas: Nang Thong, Bang Niang, Khuk Khak, Bang Sak, La On, Pakarang Cape
- `contracts.md` — Thai residential lease norms (snowbird seasonal lets), sale agreement structure, eight common gotchas including the "freehold villa" misnomer and the 30+30+30 lease promise
- `glossary.md` — Thai real-estate terminology with transliterations and English equivalents (Chanote, Tabien Baan, FET / Tor Tor 3, rai / ngan / wah land units, etc.)

## Why this case study matters

Khao Lak demonstrates the architecture working in a market with traits the original Jerusalem and Novato examples don't cover:

- **Foreign-buyer-dominant.** Most transactions in the foreign-marketed segment involve non-Thai buyers — the inverse of most Western markets.
- **Foreign land ownership prohibited.** Thai law restricts foreign land ownership; the leasehold + freehold-structure split is the standard workaround. Tests the specialist's handling of structural/regulatory factors in pricing and listings.
- **Three-plus working languages.** English, German, Russian, and increasingly Mandarin. Tests the multi-language defaults in `templates/listing.md`.
- **Resort-market thin comps.** Many sub-areas have fewer than 3 transactions per 90-day window. Tests the thin-comps acknowledgment in `frameworks/pricing.md`.
- **Coastal-hazard disclosure.** Post-2004 tsunami context shapes what a Khao Lak buyer expects to see surfaced proactively. Tests the buyer-disclosure conventions section in `region/market.md`.

## Verification status

This pack was drafted using publicly available knowledge of the Khao Lak market and Thai property law, then verified by an agent working in the region. Pricing magnitudes, current-dynamics paragraph, and tax rates flagged `[VERIFY CURRENT]` should be re-confirmed at time of use, since Thai government rate adjustments and resort-market conditions move on a quarterly cadence.

If you actively work the Khao Lak market and find gaps or inaccuracies, please open a PR.
