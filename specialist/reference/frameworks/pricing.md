# Framework — Pricing & Comp Analysis

> **Depends on:** `region/market.md` (adjustment magnitudes, seasonality, market trend), `region/regulations.md` (tax considerations).
> **Called by:** `templates/pricing-memo.md` for output structure. Conditionally calls `frameworks/international-buyers.md` for foreign-buyer demand premium.


How you arrive at a defensible list-price band. Universal across markets — adjustment **categories** are universal (this file); adjustment **magnitudes** are local (`region/market.md`).

## When to consult this file

Per `rules.md` routing: every Pricing job. Combined with `region/market.md`, `region/regulations.md`, and `templates/pricing-memo.md`.

## Inputs you need

If any are missing, stop and use `checklists/listing-intake.md` to gather them before pricing:

- Property type (SFH, apartment, multi-unit, commercial)
- Size (m² or sqft)
- Layout (BR/BA count)
- Floor (for apartments)
- Year built + last renovation date and scope
- Condition / finish level
- View, parking, outdoor space, special features
- Ownership/registration type (e.g., clean Tabu vs. Khevra Meshakenet, freehold vs. leasehold)
- Owner motivation and target list date

## Comp-set construction

Build a comp set of 3–5 sold comparables. Inclusion criteria:

| Criterion | Default |
|---|---|
| Recency | Sold within last 90 days; widen to 180 if sample is too thin |
| Geographic radius | Same neighborhood preferred; 0.5 km / 0.5 mi if necessary |
| Size band | ±15% of subject |
| Type match | Same property type (SFH ≠ townhouse ≠ apartment) |
| Layout match | ±1 BR; ±0.5 BA |
| Sale type | Arms-length only — exclude estate sales, REO, family transfers, distressed |

If you cannot get 3 comps within strict criteria, widen one criterion at a time (radius → recency → size band) and **state in the output which criterion was widened and why.**

**Thin-comp markets.** In resort markets, luxury segments, and any sub-market with low transaction volume, sub-3-comp situations are normal rather than exceptional. Don't refuse the job — produce the band, widen criteria explicitly, and **flag the band as wider than usual** to reflect the lower confidence. State sample size in the output.

## Adjustment categories — universal

These are *what* you adjust for. The actual magnitudes — per-unit dollar amounts or percentages — live in `region/market.md` under "Pricing Adjustment Magnitudes" and are filled in by the agent for their market.

Standard adjustments:

- **Size delta** — adjust per m² (or sqft) using local magnitude
- **Layout** — extra bedroom, extra bathroom, half-bath
- **Floor (apartments)** — premium per floor up in mid-rise; ground-floor adjustment (positive or negative depending on market)
- **View** — panoramic / partial / none
- **Parking** — per space; covered vs. uncovered
- **Outdoor space** — balcony / garden / roof terrace, per m²
- **Renovation level** — fully renovated vs. unrenovated, % adjustment
- **Building amenities** — elevator, gym, pool, doorman (mid/high-rise only)
- **Lot size** (SFH only)
- **Year built** — only material if significantly older than comps in a market that prices age

**Skip an adjustment** if the comp matches the subject on that dimension. Don't write "$0 adjustment" — just omit that line.

## Structural / regulatory factors (beyond standard adjustments)

In some markets, *how* a property is owned moves price as much as size or finish. Standard size/layout/finish adjustments don't capture this. Consult `region/regulations.md`. Common cases:

- **Title type within the same market.** E.g., Israel: clean Tabu-registered units vs. Khevra Meshakenet-registered. Thailand: Chanote vs. Nor Sor 3 Gor. The weaker title typically transacts at a discount even with identical specs — quantify if your comp set has both.
- **Ownership structure for foreign-marketed properties.** Leasehold vs. freehold, Thai-company-held vs. structure-only freehold, condo with foreign-quota headroom vs. condo at-cap, etc. A "freehold villa" sold to a foreigner is almost always a different structure than the same unit sold to a local — comps must match structure or be adjusted.
- **Lease remaining (leasehold markets).** A 30-year leasehold with 28 years remaining is materially more valuable than the same unit with 12 years remaining. Adjust accordingly when comps differ on this axis.
- **Encumbrances.** Liens, servitudes, restrictive covenants, juristic-person disputes (in condos) — surface and adjust if material.

When structural/regulatory factors meaningfully separate the subject from the comp set, **state this in the output** rather than rolling it silently into a generic adjustment. The agent and the seller need to see the logic.

## Band derivation

After applying adjustments to each comp, you have an adjusted comp set. From there:

1. **Midpoint.** Median or weighted-average of adjusted comps. This is your "Mid" recommendation.
2. **Range.** Typical spread is ±3–5% of midpoint. Tighter for active markets with clean comps; wider for stale or thin comp sets.
3. **Seasonality factor.** Apply per `region/market.md` (e.g., spring premium in many U.S. and European markets; summer slow in religious cities).
4. **Market-trend factor.** If 30-day comps trend up vs. the 90-day baseline, lean toward the upper band; trending down, lean lower.
5. **Foreign-buyer demand premium.** If the property is realistically marketable to foreign buyers AND the segment is verified active in `region/market.md`, see `frameworks/international-buyers.md` for whether and how to apply a premium. Never assume; verify.

## Output structure

Always produce output via `templates/pricing-memo.md`. Required elements:

- Property summary
- Recommended band (Low / Mid / High) with reasoning
- Comp set as a table
- Adjustment logic
- Market context (seasonality, trend, foreign-buyer demand if relevant)
- Caveat ("not a binding valuation; for high-stakes transactions, recommend a licensed appraisal")

## Refusals

- **Never recommend a single list price.** Always a band.
- **Never produce a band with fewer than 3 comps** without explicit acknowledgment that the sample is thin.
- **Never claim this is a binding valuation.** Always defer to a licensed appraiser for binding decisions (estate, divorce, 1031, lender requirements).

## When to redirect the question

If the agent asks for a "valuation" rather than a list price, redirect: this framework produces a defensible *list-price recommendation*, which is intentionally distinct from a binding valuation. Refer them to an appraiser for the latter.
