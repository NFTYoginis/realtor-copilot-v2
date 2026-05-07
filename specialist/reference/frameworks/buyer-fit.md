# Framework — Buyer–Property Fit

> **Depends on:** `region/neighborhoods.md` (location context), `checklists/buyer-intake.md` (buyer inputs), prior `templates/showing-note.md` outputs (if any) for citable buyer data.
> **Called by:** `templates/buyer-fit-summary.md` for output structure. Conditionally calls `frameworks/international-buyers.md` if buyer is foreign.

How you score a buyer–property match. Universal across markets.

**This is the specialist's strongest differentiator vs. raw ChatGPT.** ChatGPT pattern-matches keywords ("4BR matches 4BR"); this framework reasons about *intensity* of match, surfaces friction the buyer will feel, and tells the agent when no listing in the candidate set actually fits. Treat it accordingly — show your work.

## When to consult this file

Per `rules.md` routing: every Matching job. Combined with `region/neighborhoods.md`, `checklists/buyer-intake.md`, and `templates/buyer-fit-summary.md`.

## Inputs you need

If any are missing, stop and use `checklists/buyer-intake.md`:

- **Buyer profile** — household, budget (range + currency + financing status), geography preferences (must / nice / no-go), property type/size, lifestyle (commute, schools, observance, community), timeline, motivation, end-user vs. investor.
- **Listings to score** — 1 to N. For each: address/identifier, price, type, size, floor (apartments), key features, friction points the agent already knows.
- **Prior showing notes** *(v2)* — if the agent has run showing notes for this buyer before, cite the relevant friction themes. They override generic assumptions.

## Scoring dimensions

Score each property on **5 dimensions**:

| Dimension | What it captures | Common shallow miss |
|---|---|---|
| **Budget** | Inside the buyer's stated range, including the stretch? | Treating "asking price" as final; ignoring closing costs, taxes, HOA, expected repair. |
| **Location** | Sits in a "must" / "nice" / "no-go" geography? Distance to anchors (work, school, community)? | "It's in [neighborhood]" without checking the *specific corner* — schools shift by 4 blocks, walkability collapses across an arterial. |
| **Type/size** | Apartment vs. house; bedroom count; bath count; outdoor space; parking. | Counting bedrooms without checking *usable* layout (a 4th BR that's a converted closet doesn't function as one). |
| **Lifestyle** | Commute, schools, observance, community fit, neighborhood character. | Generic schools-are-good; missing the community-specific anchor (e.g., walking-distance shul/mosque/parish, French-speaking school, recovery-friendly neighborhood). |
| **Friction** | Walk-up vs. elevator, ground-floor exposure, noise, parking access, daily-wearing costs. | Missing the *daily* cost. A walk-up with two young kids and weekly groceries is wearing in a way a one-tour visit can't surface. |

## Scoring scale

Per dimension, assign one of:

- **Clear** — meets or exceeds the buyer's preference. No friction.
- **Acceptable** — works, with some tradeoff. Buyer would not be unhappy.
- **Friction** — works, but with a real cost the buyer will feel. **Must call this out by name.**
- **Blocker** — disqualifies the property. Don't waste a showing.

A property's **overall fit** = the worst score across the 5 dimensions, modulated by the buyer's stated weights (below). A single "Blocker" rules out the property regardless of other "Clear" scores.

## Weight defaults by buyer type

Adjust the importance of dimensions based on buyer type:

| Buyer type | Heaviest dimensions | Common dimension to deprioritize |
|---|---|---|
| Family with school-age kids | Lifestyle (schools), Location (walkability), Type/size (BR count) | Friction below other concerns — kids adapt |
| Empty-nesters / downsizers | **Friction** (no walk-up, no stairs), Location, Lifestyle | Type/size — they're getting smaller on purpose |
| Investor — yield | Budget, Location, Type/size — lifestyle ignored unless it affects rentability | Lifestyle |
| Investor — capital appreciation | Location, Type/size, market trajectory from `region/market.md` | Friction (renter problem, not theirs) |
| First-time buyers | Budget, Friction (resale risk too), Lifestyle | Type/size — they're often stretching |
| Returning diaspora / relocating expats | Lifestyle (community/language), Location, then everything else (see `frameworks/international-buyers.md`) | Budget often less constrained than locals' |

If the buyer doesn't fit a row cleanly, infer weights from their stated motivations and *say so* in the output: "I'm weighting Friction heavily because you mentioned daily commute fatigue."

## Show your work — required reasoning chain for the top pick

For the #1 ranked property, the output must include a per-dimension justification, **not just the score**. For each of the 5 dimensions:

1. State the buyer's preference for that dimension (one phrase, citing the intake or showing note).
2. State what this property offers (one phrase).
3. State the gap, if any, and what it costs the buyer in daily life.
4. Score.

This is the difference between "Listing C: Clear / Acceptable / Clear / Clear / Friction → Acceptable" (useless) and a paragraph the agent can hand to the buyer as a reasoned recommendation.

## When the data is thin

If the buyer profile or listings are under-specified, **say so before scoring**. Do not infer to fill gaps.

Acceptable: "Buyer didn't specify school requirements. I've assumed neutral on schools given they have no kids — confirm if this is wrong before relying on the rank."

Not acceptable: silently assuming and ranking.

## When no listing fits

If no listing in the candidate set scores above "Acceptable" on the buyer's heaviest dimensions, **tell the agent that explicitly.** Recommend going back to sourcing rather than showing the buyer something that won't work.

Phrasing: "None of these three is a strong fit for this buyer. Listing B is the closest, but it sits at Friction on Lifestyle (the dominant dimension here). Worth re-sourcing before booking showings — happy to score new candidates."

## Citing prior showing notes (v2)

If the agent has captured showing notes for this buyer (via `templates/showing-note.md`), cite the relevant friction themes by tag:

> "Per the showing note from [date] at [address], buyer flagged `ground-floor-bedrooms` as friction. Listing B has the same configuration — likely a repeat issue."

Showing-note tags carry more weight than generic intake assumptions because they reflect what the buyer actually said in front of a property, not what they imagined they wanted in an intake call.

## Output structure

Always produce output via `templates/buyer-fit-summary.md`. Required elements:

- Buyer profile summary (1 paragraph)
- Listings ranked (table) — overall fit + key reason per listing
- Detailed scoring for the top pick (table per dimension + reasoning chain per the "Show your work" section above)
- Top recommendation + reasoning
- Honest tradeoff (what the buyer compromises on for the top pick)
- "Don't dismiss yet" section if the #2 listing has a real case
- Citations to prior showing notes by tag, if any

## Honesty principle

**Always call out friction. Never inflate a fit to push a property.**

The agent reads this output before deciding which property to show first. If you over-score a property to get it to the top, you cost them a wasted showing and a bruised client relationship. Friction visible upfront is always better than friction surfaced at the showing.

If you find yourself softening a real concern to make the rank work, stop and re-rank.
