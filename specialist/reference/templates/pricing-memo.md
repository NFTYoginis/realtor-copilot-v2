# Template — Pricing Memo

Output structure for the pricing job. Always follow this structure.

## When to consult this file

Per `rules.md`: every pricing job.

## Required sections (in this order)

### 1. Property summary

One paragraph. The property's specs + the question being answered. Include type, size, layout, condition, neighborhood, and the agent's stated timeline or motivation.

### 2. Recommended band (table)

| Band | Price | When to use |
|---|---|---|
| Low | [price] | [1-line rationale — typically: speed, quick offers expected] |
| **Mid** | **[price]** | **Default recommendation.** [1-line rationale] |
| High | [price] | [1-line rationale — typically: only if 30-day comps trend upward] |

Followed by a 1–3 sentence reasoning paragraph. Anchor to the comp set's adjusted midpoint.

### 3. Comp set (table)

| # | Beds/Baths | Size | Sale price | $/unit | Sale date | Adjustments to subject |
|---|---|---|---|---|---|---|
| 1 | [layout] | [size] | [price] | [$/m² or $/sqft] | [date] | [+/- adjustments with brief reason] |
| 2 | ... | ... | ... | ... | ... | ... |
| 3 | ... | ... | ... | ... | ... | ... |

Minimum 3 comps per `frameworks/pricing.md`. If fewer, state which inclusion criterion was widened and why.

After the table: state the **adjusted comp midpoint** as a single number.

### 4. Adjustment logic

2–4 bullets. Categories used (per `frameworks/pricing.md`); magnitudes (per `region/market.md`). Note any unusual adjustments and why they were applied.

### 5. Market context

3 short bullets:
- Inventory and demand dynamics (current quarter)
- Seasonality (per `region/market.md`)
- Foreign-buyer demand — only if relevant to this property (see `frameworks/international-buyers.md`)

### 6. Caveat

"This is a defensible list-price recommendation, not a binding valuation. For high-stakes transactions (estate, divorce, 1031, lender requirements), recommend a licensed appraisal. Verify [specific items] before final listing."

The "specific items" should call out anything the comps couldn't fully account for — roof condition, recent renovation permits, ownership-registration status, anything flagged in `region/regulations.md` or `region/contracts.md` that affects price.

## Refusals (from frameworks/pricing.md)

- Never recommend a single list price. Always a band.
- Never produce a band with fewer than 3 comps without acknowledgment that the sample is thin.
- Never claim this is a binding valuation.
