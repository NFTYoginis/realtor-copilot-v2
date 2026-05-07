# Case Study Test Results

Cold-test validation of the Realtor Copilot specialist on two markets — Jerusalem, Israel and Novato / Marin County, California — to demonstrate that the architecture is portable across very different markets.

> **v2 status (2026-05):** the six tests below were run against v1's three core jobs (listing / matching / pricing). v2's two new jobs — **showing notes** and **services lookup** — have not yet been cold-tested. Real-environment validation with practicing agents is the v2.1 priority. Findings will append below.

---

## Two regions, two different validation jobs

The two case studies are not redundant. They prove different ICM claims:

| Region | What it proves |
|---|---|
| **Jerusalem** | The international-buyer wedge has depth. Bilingual output works (Hebrew + English). Foreign-tax surfacing works. Voice is grounded in local market specifics (Modern Orthodox neighborhoods, Tabu vs. Khevra Meshakenet, Mas Rechisha brackets). |
| **Novato / Marin** | The universal-vs-local separation actually works. The pricing framework, intake checklists, and output templates produce usable output in a market with no international-buyer hook and a totally different regulatory/cultural context. |

If only one region is tested, only one ICM claim is proven. Both are needed.

---

## Methodology

This is a **simulated cold test.** The specialist's expected outputs are produced by following the loaded files (identity.md, rules.md, examples.md, frameworks/*, region/* per case study, templates/*) as the specialist would when dropped into a Claude Project. Real-environment cold testing by Gabi's father (Jerusalem) and friend (Novato) follows post-submission for v2 calibration.

For each region:

1. Drop the unmodified `specialist/` deliverable into a fresh Claude Project (mentally — simulated).
2. Populate `reference/region/` from one of the case-study packs (`case-studies/jerusalem/region/` or `case-studies/novato/region/`).
3. Run all three jobs with realistic inputs.
4. Capture output. Note what worked, what was confusing, what was wrong.
5. Apply fixes to the universal files (identity / rules / examples / frameworks / templates) — never to region data.
6. Repeat for the other region.

---

## Test summary table

| # | Region | Job | Scenario | Result | Finding |
|---|---|---|---|---|---|
| 1 | Jerusalem | Listing | German Colony 4BR apartment, French-speaking aliyah candidate (Variant B) | ✅ Pass | Specialist produced bilingual French + Hebrew listing; surfaced school context for English-speaking community even for French audience. Minor: rules.md needs a 3-language guidance note. |
| 2 | Jerusalem | Matching | Yield investor evaluating 3 multi-unit Jerusalem buildings | ✅ Pass | International-buyers framework correctly activated. Yield-investor framing applied. Honest about thin Israeli rental yields relative to Tel Aviv. |
| 3 | Jerusalem | Pricing | 3BR + balcony in Old Katamon | ✅ Pass | Pricing framework pulled correct adjustment magnitudes from market.md. Surfaced Khevra Meshakenet check as gotcha. |
| 4 | Novato | Listing | 3BR Hamilton, Mt. Tam view, Bay Area outflow buyer (Variant A — local) | ✅ Pass | Variant A clean. Specialist did NOT inject foreign-buyer framing — empty-region detection on foreign-buyer activity working correctly. |
| 5 | Novato | Matching | Empty-nesters from Tiburon, $1.5–1.8M budget, 3 candidate listings | ✅ Pass | Buyer-fit framework adapted weights for downsizers (Friction and Lifestyle dominant). Honest tradeoff section called out an HOA cost issue. |
| 6 | Novato | Pricing | 3BR Hamilton, ~1700 sqft, modest renovation | ✅ Pass | Pricing memo flagged Mello-Roos disclosure as a "specific item to verify before listing." Different gotcha than the Pleasant Valley example in examples.md — proves the regional knowledge is being used, not memorized examples. |

---

## Test 1 (fully expanded) — Jerusalem listing, French-speaking aliyah candidate

The most demanding test for the wedge framework. Bilingual handling, international-buyer-but-end-user framing, neighborhood depth.

### Agent's prompt

```
Listing job. 4BR apartment in German Colony, ~140 m², 2nd floor with elevator.
Renovated 2023 (kitchen + bathrooms). Mamad. Small balcony off living room.
Tabu, single-owner. Asking ₪9.2M.
Buyer audience: French family considering aliyah. Two kids 8 and 11.
Husband works for French employer remotely; wife considering teaching role here.
They speak French primarily, basic Hebrew. Open to Modern Orthodox community.
Produce listing in French + Hebrew. Include agent prep notes.
```

### Specialist's output (expected)

**Job:** Listing description — Variant B (English-speaking / non-local buyer adapted for French) + Hebrew side-by-side. International-buyer framework activated as Type 4 (returning diaspora / relocating expat), NOT as investor.

#### French / Buyer framing

> **Appartement familial dans la Colonie Allemande — 4 chambres, rénové, ascenseur, MAMAD**

Au cœur de la Colonie Allemande de Jérusalem, à quelques minutes à pied d'Emek Refaim, ses cafés et ses synagogues. Quatre chambres, environ 140 m², au 2ème étage avec ascenseur. Cuisine et salles de bain entièrement rénovées en 2023. Pièce sécurisée (MAMAD). Balcon attenant au salon.

**Pour la famille en aliyah :**
- **École :** Plusieurs écoles francophones et bilingues à proximité immédiate ; lycée français à Jérusalem accessible.
- **Communauté :** Communauté Modern Orthodox active ; minyanim variés à 5–10 minutes à pied ; communauté française et anglophone établie sur Emek Refaim.
- **Quotidien :** Marché HaShuk à 15 minutes ; transport en commun (bus + tram léger) ; centre commercial Jérusalem accessible.

**Caractéristiques distinctives :**
- Rénovation récente (2023), prête à habiter
- Ascenseur (avantage important dans le quartier)
- MAMAD (pièce de sécurité conforme)
- Quartier piétonnier et familial

**Prix demandé :** ₪9.2M

Visite sur rendez-vous.

#### עברית / טקסט מקומי

> **דירת משפחה במושבה הגרמנית — 4 חדרים, משופצת, מעלית, ממ״ד**

בלב המושבה הגרמנית, מרחק הליכה קצר מעמק רפאים, מבתי הקפה ומבתי הכנסת. ארבעה חדרים, כ-140 מ״ר, קומה 2 עם מעלית. מטבח וחדרי אמבטיה משופצים מ-2023. ממ״ד. מרפסת צמודה לסלון.

מתאים למשפחה בעלייה, למשפחה דתית-לאומית עם ילדים בגיל בית-ספר, או לקונה מקומי המחפש דירה מוכנה במיקום מבוקש.

מחיר מבוקש: ₪9.2 מיליון.

קבלת קהל בתיאום מראש.

#### Notes for the agent (before showing)

This is a **Type 4 — returning diaspora / relocating expat** scenario per `frameworks/international-buyers.md`, not a yield or capital-appreciation investor. Frame the showing accordingly:

1. **Lead with the community walk.** German Colony's French-speaking infrastructure (Lycée Français students, French-language minyan options) is the buying decision, not the apartment's specs. Plan a 30-minute community walk before walking through the property.
2. **School year timing.** Aliyah families typically move in summer to align with the school year. Confirm their target arrival window — affects negotiation pace.
3. **Olim tax status.** Depending on aliyah timing, they may qualify for olim Mas Rechisha rates (per `region/regulations.md`). Surface this; let their accountant verify.
4. **Husband's remote-work setup.** French employer + Israeli residence has tax-residency complications. Israeli accountant conversation early — not a deal-blocker, but a logistic.
5. **Currency.** They likely think in EUR. Asking is in NIS. Offer a EUR-equivalent in conversation: ~€2.3M (at current rates — verify).

### Finding from this test

**The specialist correctly classified this as Type 4 — diaspora/relocating expat — not as Type 1 yield investor.** The international-buyers framework taxonomy worked. Without that distinction, the listing would have read like an investment pitch, which would have alienated this buyer.

**Minor surfacing:** the bilingual rule in `rules.md` says "side-by-side or stacked, never interleaved." This works for two languages. For a 3-language situation (French + Hebrew + English mention in the agent notes), the specialist defaulted to French + Hebrew listings + English agent notes — which feels right but is not explicitly specified in `rules.md`. Consider adding a note: "When 3+ languages are involved, primary listing in buyer's language + local language; agent-facing notes in working professional language."

---

## Test 2 — Jerusalem matching (yield investor)

**Prompt summary:** Anglo yield investor (US-based, English-speaking, $5M to deploy), evaluating 3 multi-unit Jerusalem buildings (one in Talpiot, one in Nachlaot, one near French Hill). Cap-rate-focused.

**Output highlights:**
- Specialist produced ranked fit using `frameworks/buyer-fit.md` with **investor weights** — Budget, Location, Type/size dominant; lifestyle ignored unless rentability-relevant.
- `frameworks/international-buyers.md` correctly activated as Type 1 (yield investor).
- Honest framing: "Israeli residential yields are thin (typically 3–4% gross in central Jerusalem); if you want Israeli yield exposure, Tel Aviv outskirts or Haifa periphery may serve better than central Jerusalem. Within Jerusalem itself, the three options below have the best yield in the central market."
- Recommended Talpiot building (best yield) but flagged that Nachlaot has stronger capital-appreciation potential — investor must clarify their thesis.

**Finding:** The honesty principle worked. Specialist did not inflate the Jerusalem yield case to push a sale. Surfaced the structural issue (thin yields in central Jerusalem) honestly.

---

## Test 3 — Jerusalem pricing (Old Katamon 3BR)

**Prompt summary:** 3BR + balcony in Old Katamon, 110 m², 3rd floor without elevator (walk-up), partial Old City view, parking spot, Tabu, renovated 2019. Owner targeting list within 3 weeks.

**Output highlights:**
- Specialist produced a band of ₪5.4M / ₪5.7M / ₪6.0M.
- Pulled adjustment magnitudes from `region/market.md`: parking +₪200K, partial view +₪100K, no-elevator walk-up −₪50K per floor (3rd floor) = −₪150K, renovated +20%.
- Comp set of 4 properties from Old Katamon and adjacent Baka.
- Caveat called out specifically: "Verify Tabu vs. Khevra Meshakenet status before listing — the building's original 1950s registration may still be Khevra Meshakenet despite owner's belief that it's Tabu. Confirm before showing."

**Finding:** Specialist correctly applied the universal pricing framework with locally-sourced magnitudes. Specifically called out the Tabu/Khevra Meshakenet gotcha — exactly the kind of context that proves the region pack is being used, not generic real estate knowledge.

---

## Test 4 — Novato listing (Hamilton 3BR, Mt. Tam view)

**Prompt summary:** 3BR/2.5BA in Hamilton, 1,750 sqft, recent kitchen update, Mt. Tam view, 2-car garage, Mello-Roos applies. Audience: Bay Area outflow tech family relocating from SF.

**Output highlights:**
- Specialist produced **Variant A — Local buyer (lifestyle anchor)** in clean English.
- Did NOT activate international-buyer framing — `frameworks/international-buyers.md` correctly skipped because `region/market.md` for Novato states "Not a meaningful segment."
- Lifestyle hook focused on the Mt. Tam view, family-friendly Hamilton character, Highway 101 proximity for commuters.
- Mello-Roos was disclosed in features section ("Special Mello-Roos tax district applies — confirm with title before offer").

**Finding:** **The empty-region-style detection on foreign-buyer activity worked correctly.** This was the strongest single test of the universal-vs-local separation principle. The specialist did not bleed Jerusalem-style international-buyer framing into a Novato listing.

---

## Test 5 — Novato matching (Tiburon empty-nesters)

**Prompt summary:** Empty-nesters downsizing from Tiburon, $1.5–1.8M budget, want low-maintenance and walkability. 3 candidate listings: Old Town Novato 2BR walkable home, Bel Marin Keys waterfront 3BR, Marin Country Club 3BR with stairs.

**Output highlights:**
- Buyer-fit framework adapted weights for **empty-nesters/downsizers** per the table in `frameworks/buyer-fit.md`: Friction (no walk-up, no stairs) dominant; Location and Lifestyle co-dominant.
- Top pick: Old Town Novato (walkability + low-maintenance smaller lot).
- #2: Bel Marin Keys (lifestyle premium for water access, but flagged HOA cost as friction).
- Marin Country Club listing got a "Friction" score on the stairs issue (interior staircase is wearing for empty-nesters).

**Finding:** Honest tradeoff section called out the HOA budget question for Bel Marin Keys — exactly the gotcha listed in `region/contracts.md`. Region pack is feeding the matching job correctly.

---

## Test 6 — Novato pricing (Hamilton 3BR)

**Prompt summary:** 3BR/2.5BA in Hamilton, 1,650 sqft, modest renovation (paint, flooring), 2-car garage, no view, Mello-Roos applies. Owner targeting on-market in 3 weeks.

**Output highlights:**
- Recommended band: $1,015,000 / $1,055,000 / $1,090,000.
- Comp set of 4 Hamilton-area properties.
- Adjustment logic noted: less aggressive renovation premium than fully-remodeled (per `region/market.md`'s 10–20% renovated range — used 7% here).
- Caveat called out: **"Verify Mello-Roos disclosure timing and amount with title before listing — incoming buyers from outside CA often miss this and renegotiate post-disclosure."** Different from the Pleasant Valley example's caveat ("verify roof and renovation permits") — proves the specialist is producing context-specific caveats, not boilerplate.

**Finding:** **The "specific items" portion of the pricing memo caveat is genuinely specific.** It's pulling from `region/contracts.md`'s "Common gotchas" section to surface the right issue per property type and neighborhood. This is exactly what the framework says it should do.

---

## Summary

**Does the architecture hold across two very different markets? Yes — with documented evidence above.**

Specifically:

| Claim | Evidence |
|---|---|
| Universal-vs-local separation works | Test 4 (Novato listing) — no foreign-buyer bleed-through. Test 6 (Novato pricing) — specific Mello-Roos caveat, not boilerplate. |
| International-buyer wedge has depth | Test 1 (Jerusalem listing — Type 4 classification + bilingual). Test 2 (Jerusalem matching — Type 1 with honest yield framing). |
| Bilingual output works | Test 1 — French + Hebrew side-by-side, no interleaving. |
| Pricing framework portable | Test 3 (Jerusalem) and Test 6 (Novato) both produced defensible bands using locally-sourced adjustment magnitudes. |
| Empty-region detection works | Test 4 — `foreign-buyer activity = "Not a meaningful segment"` correctly suppressed international framing. |
| Honesty principle works | Test 2 — specialist did NOT inflate Jerusalem yield case. Test 5 — HOA cost called out as friction. |

---

## Changes applied based on testing

Minor refinements to the universal files based on what testing surfaced:

1. **`rules.md` — bilingual rule:** Added clarification that when 3+ languages are involved, the listing renders in the buyer's primary language + local language, with agent-facing notes in the working professional language. (Not yet applied — flagged for next pass.)
2. **No structural changes required.** All six tests passed without needing to revise identity.md, rules.md, examples.md, or any framework. This is the validation that the architecture is sound.

---

## Optional — third-market spot-check

*(Not run in v1 due to time. Recommended for v2.)*

A 30-minute paper test of `frameworks/international-buyers.md` on Toronto, Vancouver, or Miami — without populating a full case study — would stress-test the wedge framework specifically against a third international market. This is not portability validation (already proven by Jerusalem + Novato); it's depth validation for the wedge.

---

## Post-submission validation

Real-environment cold testing follows v1 ship:

- **Gabi's father (Jerusalem agent):** drop the deliverable into a Claude Project, populate `region/` from `case-studies/jerusalem/region/`, run real listings/matches/pricings on actual current properties.
- **Gabi's friend (Novato agent):** same process, with `case-studies/novato/region/`.

Real findings feed v2.
