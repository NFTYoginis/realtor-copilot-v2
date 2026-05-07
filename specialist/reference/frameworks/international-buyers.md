# Framework — International / Foreign Buyers

> **Depends on:** `region/market.md` (foreign-buyer activity verification), `region/regulations.md` (foreign-buyer tax exposure).
> **Called by:** `templates/listing.md` Variant C (international investor); `frameworks/buyer-fit.md` (when buyer is foreign); `frameworks/pricing.md` (foreign-buyer demand premium check).


The wedge. Specialized framework for international buyers. They think differently from local buyers, value differently, transact differently. Generic real-estate advice will under-serve them.

## When to consult this file

Per `rules.md` routing:

- **Listing job** — when the agent specifies an international audience, OR when the buyer pool for the property realistically includes foreign buyers (per `region/market.md`'s "Foreign Buyer Activity" section).
- **Matching job** — when the buyer is a foreign citizen or non-resident.
- **Pricing job** — only when assessing whether a foreign-buyer demand premium applies to the property (called from `frameworks/pricing.md`).

When in doubt, **ask the agent** whether to apply the international-buyer framing. Defaulting to "yes" can produce listings that feel out of place for a local-buyer pool.

## Buyer-type taxonomy

Foreign buyers are not one segment. The framing for each type is materially different.

### Type 1 — Yield investor

- **What they want.** Predictable cash flow. Stabilized buildings, multi-unit, occupied. Less interest in location prestige; more interest in occupancy, rent roll, management.
- **What they ask about.** Cap rate, gross yield, net yield (after fees and taxes), tenant turnover, rent growth.
- **Decision pace.** Faster than other foreign-buyer types if the numbers are clean. Slower than locals because of remote-due-diligence overhead.
- **Listing framing.** Lead with the yield, then the property. Investment summary table early. Tax considerations explicit. Exit liquidity addressed.

### Type 2 — Capital-appreciation investor

- **What they want.** Asymmetric upside. Tier-1 location, scarce asset class (e.g., Mandate-era stone in Jerusalem; pre-war in NYC; heritage in old European centers).
- **What they ask about.** Comparable transactions, supply constraint, market trajectory, hold liquidity.
- **Decision pace.** Slower. They're buying a thesis, not a number. Expect multiple meetings.
- **Listing framing.** Lead with the scarcity thesis. Comps. Long-term market dynamics. Cap rate is secondary.

### Type 3 — Lifestyle / legacy buyer

- **What they want.** A second home, an inheritance asset, a foothold in a country they care about. Use case is part-time / vacation / future relocation.
- **What they ask about.** Neighborhood, community, language environment, services for non-residents, property management (because they won't be there full-time).
- **Decision pace.** Highly variable — emotional and relationship-driven.
- **Listing framing.** Lifestyle and location-anchored, but with practical part-time-use info: management options, security when empty, utility setup, taxes for non-residents.

### Type 4 — Returning diaspora / relocating expat

- **What they want.** A home in a place they have an identity connection to. Often family-driven (kids' school, religious community, language, parents nearby).
- **What they ask about.** Community, schools, religious infrastructure, language environment.
- **Decision pace.** Family-cycle paced (school year, life event).
- **Listing framing.** Lifestyle-first, like a local end-user, but with extra context an outsider needs to evaluate the lifestyle (how to assess the school, how to know which religious community is right for them, etc.).

## Framing differences vs. local buyers

| What local buyers want | What foreign buyers also need |
|---|---|
| Lifestyle hook | Investment context (yield, appreciation thesis, exit) — for investor types |
| Neighborhood vibe | Community/language environment — for end-user types |
| Listing in local language | Listing in their working language (English most often; sometimes Mandarin, French, Russian) |
| Currency in local denomination | Currency in their working currency (USD, EUR, GBP) — often both |
| Tax basics assumed | Foreign-buyer tax exposure surfaced — see `region/regulations.md` |
| Standard contract path | Power-of-attorney noted; AML / source-of-funds path noted as next-step |

## Documentation considerations (for agent prep, not buyer-facing)

Surface these as agent-prep notes — not as content for the buyer:

1. **Residency status of the buyer.** Tax treatment differs. Confirm before the showing.
2. **Source of funds.** AML rules in most markets require this. Better surfaced early than late.
3. **Power of attorney.** Most non-resident buyers will close remotely. Local notary requirements apply.
4. **Identity documentation.** Passport + visa status; for some markets, additional documents.

## Communication considerations

- **Time zones.** Multi-day async loop is the norm, not single-call decisions. Plan touchpoints accordingly.
- **Language.** Confirm the buyer's working language. Use it consistently. If using an intermediary (translator, family member, agent on the buyer's side), clarify roles before the meeting.
- **Decision pace.** Most foreign buyers are slower than locals. Build the pacing into expectations — plan for 3–5 substantive touchpoints, not one closing call.
- **Cultural framing.** Don't generalize across "foreign buyers" — specifics matter (a French buyer is not the same as a Chinese buyer is not the same as an Anglo investor). Where you can, point the agent at concrete cultural cues; where you can't, say so.

## Pricing-premium considerations

Foreign-buyer demand can support a premium **only if all three** are true:

1. The local segment is verified active in `region/market.md`'s foreign-buyer activity section.
2. The property has features that match foreign-buyer preferences (location prestige, scarcity, clean title, rentability).
3. The agent has comparable foreign-buyer transactions to anchor the premium.

**Never assume a foreign-buyer premium without evidence.** Pricing flows back through `frameworks/pricing.md` — the international-buyer demand factor is one input there, not a license to inflate.

## Honesty principle

Foreign buyers often pay a premium AND face friction (longer closes, more paperwork, less negotiation flexibility). **Surface both.** An agent who promises an easy foreign close and delivers a 6-month process loses the deal at month 4.

When the property is *not* a good fit for foreign buyers — typical local-buyer asset, no feature that matters to foreigners — say so. Don't inflate the international angle to make a listing sound bigger than it is.
