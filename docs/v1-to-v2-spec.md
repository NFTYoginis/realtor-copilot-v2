# Realtor Copilot — v1 to v2 Specification & Changelog

Comprehensive technical and product changelog for the writing team. Use this to compose articles, blog posts, or technical breakdowns without re-reading the full repository.

**Document audience.** Writers and editors covering the product. Assumes general literacy with software and AI assistants; does not assume real-estate expertise.

---

## 0. Executive summary

Realtor Copilot is a free, open-source AI specialist for residential real-estate agents, distributed as a folder of markdown files that drops into a Claude Project. v1 shipped May 2026 with three jobs (listing description, buyer-property fit ranking, pricing with comps). v2 (also May 2026) expands to five jobs, adds a welcome menu, sharpens the buyer-fit reasoning, and introduces cross-job memory via showing notes that future jobs can cite.

The architecture is called **Interpretable Context Methodology (ICM)** — folders as architecture, files as the program. The architecture is intentionally portable: switching markets edits exactly one folder.

---

## 1. The problem space

### What residential real-estate agents actually do

A working agent's week breaks into roughly:

1. **Listing work** — writing listing copy, prepping marketing materials, positioning a property to the right buyer pool.
2. **Buyer-side work** — intaking buyer profiles, sourcing properties, running showings, negotiating offers.
3. **Pricing / valuation** — pre-listing conversations with sellers ("what should we list at?"), comp pulls, comparative market analyses (CMAs).
4. **Communication** — emails, texts, status updates with sellers and buyers.
5. **Process management** — checklists for listing, transaction, closing.
6. **Administrative** — vendor coordination (inspectors, lenders, stagers), referrals, CRM updates.
7. **Business development** — relationship-building, marketing the agent's own brand, generating relo and referral leads.

### Where AI helps and where it doesn't

The 2025 NAR Technology Survey (n=1,241) found:

- 68% of agents have used AI; 20% daily, 22% weekly.
- Tool share: ChatGPT 58%, Gemini 20%, Copilot 15%.
- Self-reported impact: 17% significant positive, 33% moderate, **46% no meaningful impact.**

The most-cited friction in trade press (Inman, RISMedia) is *prompting skill* and *workflow* — agents type into ChatGPT and get generic answers because they don't know how to scaffold the request. This is the exact gap a structured prompt specialist closes.

### What the competitive landscape looks like (2025–2026)

- **Bundled AI in CRMs** — Lofty (~$499–$1,500/mo), Follow Up Boss (~$58–$83/seat/mo), Top Producer, Rechat, kvCORE, CINC ($899+/mo). All ship some form of AI assistance.
- **Standalone listing-copy generators** — Listings.ai, HAR.com AI Description, etc. Saturated; ChatGPT is the de-facto default.
- **CMA / pricing tools** — Saleswise, CMAGPT, iCMALive, RPR AI CMA. ~5 dedicated AI products.
- **Buyer–property fit ranking** — no clear standalone leader. **White space.**
- **Showing-notes / audio-to-doc for solo agents** — sparse, mostly bundled into CRMs (Rechat AI Memo, Renewator). White space for off-CRM agents.
- **Local-services KB** — does not exist as a product category. Today this is a personal Rolodex or CRM contacts table.

Realtor Copilot's defensible wedge is the white-space jobs (matching, pricing reasoning, showing notes, services lookup) plus the cost structure (free, no install).

---

## 2. v1 — what shipped

### v1 architecture summary

- **17 markdown files**, ~1,400 lines total.
- Three jobs: listing description, buyer-property matching, pricing band.
- Distributed as a folder. Agent uploads to a Claude Project. ~20-minute setup to populate 5 region files.
- Three populated case studies: Jerusalem, Novato (Marin County), Khao Lak.
- MIT licensed, public on GitHub at `NFTYoginis/realtor-copilot`.

### v1 file map

```
specialist/
├── identity.md          who Claude becomes
├── rules.md             routing logic per job
├── examples.md          three example interactions
├── reference/
│   ├── region/          local market data (5 files — agent populates)
│   │   ├── market.md
│   │   ├── neighborhoods.md
│   │   ├── regulations.md
│   │   ├── contracts.md
│   │   └── glossary.md
│   ├── frameworks/      universal logic
│   │   ├── pricing.md
│   │   ├── buyer-fit.md
│   │   └── international-buyers.md
│   ├── checklists/      structured intake
│   │   ├── listing-intake.md
│   │   └── buyer-intake.md
│   └── templates/       output structures
│       ├── listing.md
│       ├── buyer-fit-summary.md
│       └── pricing-memo.md
└── README.md
```

### v1 design principles

1. **Three jobs, politely redirect anything else.** Discipline is the moat. Marketing copy generators, comms drafts, mass outreach are explicitly out of scope.
2. **The agent is the user; you assist, the agent decides.** Voice rule: "You should consider listing this at..." — never "I'd list this at..."
3. **Always a band, never a number.** Pricing output is always low/mid/high with comp logic. No single-number list price.
4. **Honest about friction.** The buyer-fit framework requires calling out friction explicitly; never inflate a fit to push a property.
5. **Don't speak to the agent's clients.** All output is for the agent's use; nothing addressed to clients.
6. **Universal vs. local separation.** Universal logic in `frameworks/`, `templates/`, `checklists/`, `identity.md`, `rules.md`; local data in `region/`. Switching markets edits one folder.
7. **Templates ARE the output structure.** Not background context — the file in `templates/` is the literal output shape.

### v1 jobs in detail

#### Job 1 — Listing description

Input: property specs + audience (local end-user / English-speaking / international investor) + bilingual flag if local market needs it.

Output: a finished listing in the audience's primary language, with side-by-side or stacked local-language version when applicable. International-investor variant adds yield framing, foreign-tax surfacing, source-of-funds note, exit liquidity note.

Routing: `region/market.md`, `region/neighborhoods.md`, `checklists/listing-intake.md`, `templates/listing.md`. If international: `frameworks/international-buyers.md` + `region/regulations.md`.

#### Job 2 — Buyer–property matching

Input: buyer profile + 1–N candidate listings.

Output: ranked-fit table, detailed scoring on the top pick across 5 dimensions (Budget / Location / Type-size / Lifestyle / Friction), top recommendation, honest tradeoff, "don't dismiss yet" callout if #2 has a real case.

Routing: `region/neighborhoods.md`, `checklists/buyer-intake.md`, `frameworks/buyer-fit.md`, `templates/buyer-fit-summary.md`. If international buyer: `frameworks/international-buyers.md`.

#### Job 3 — Pricing & comp analysis

Input: property specs + owner timeline + recent comp data (or request to use the local market file's adjustment magnitudes).

Output: defensible band (Low / Mid / High), comp set table, adjustment logic, market context, single short caveat.

Routing: `region/market.md`, `region/regulations.md`, `frameworks/pricing.md`, `templates/pricing-memo.md`.

### v1 case studies

- **Jerusalem, Israel** — proves the international-buyer wedge has depth (Tabu vs. Khevra Meshakenet title, Mas Rechisha tax brackets, Modern Orthodox community geography, multilingual output).
- **Novato / Marin County, CA** — proves the universal logic works without any foreign-buyer hook (Mello-Roos, hillside foundations, Bay Area outflow buyers).
- **Khao Lak, Thailand** — coastal resort, foreign-buyer-dominant, leasehold/freehold structure, multi-language (English / German / Russian / Mandarin).

### v1 validation status

`case-studies/test-results.md` documents six tests across Jerusalem and Novato. **Critically: this is a *simulated* cold-test — the document is explicit that real-environment validation by practicing agents is post-ship.** Real cold-tests are pending with the author's father (Jerusalem agent) and friend (Marin agent).

---

## 3. Why v2 — what drove the changes

### Domain insight from the author (former real-estate practitioner)

The author surfaced the actual workflow gaps after v1 shipped. The list:

1. Listing descriptions ✓ (already in v1)
2. Property marketing materials (flyers, IG posts, "just listed" cards)
3. Seller/buyer comms (status updates, follow-ups)
4. Coming-soon outreach to local realtors (pre-MLS interest)
5. Listing checklists and closing checklists (process trackers)
6. Mass agent-to-agent relo expert outreach
7. Showing notes from audio dictation
8. Local-services KB (inspector, lender, handyman)

### Decision framework applied

Not all eight earned a place in v2. The decision framework was:

| Idea | Verdict | Reason |
|---|---|---|
| Listing descriptions | Keep (already shipped) | Job 1 |
| Property marketing materials | Skip | Red ocean — Listings.ai, Canva, every CRM ships this. ChatGPT is the de-facto default. |
| Seller/buyer comms drafts | Defer | CRM territory (Follow Up Boss, Lofty). Voice-rule risk. |
| Coming-soon outreach drafts | Defer | Same as above. |
| Listing/closing checklists | Skip | Closer to Notion templates than LLM jobs; the specialist isn't a process tracker. |
| Mass agent cold outreach | **Reject** | Spam-adjacent regardless of copy quality. Damages reputation. CAN-SPAM exposure. |
| Showing notes | **Add** | White space for solo agents off-CRM. Compounds matching and pricing as citable input. |
| Local-services KB | **Add** | White space (no product category exists). Fits region/ pattern perfectly. Sticky once curated. |

### Market research findings that drove final decisions

External research (NAR 2025 survey, Inman/RISMedia coverage, competitor pricing) confirmed:

- **Buyer–property fit ranking with reasoned friction** is the white-space differentiator. Sharpen `frameworks/buyer-fit.md`.
- **42% of agents use AI weekly** but only 17% see significant impact. The disappointed cohort cites prompting friction. **They are the v2 user.**
- **Free + no-install bypasses** the $500–$1,500/mo CRM buying cycle. Distribution moat.
- **Showing-notes for solo agents off-CRM** is modest white space — small but meaningful, especially when it compounds matching/pricing.

---

## 4. v2 — what's new

### 4.1 Welcome menu (first-turn behavior)

**New file:** `specialist/welcome.md`.

**Behavior:** On the first turn of a new conversation, the copilot greets the agent and presents a menu of the five jobs. Skipped automatically if the agent's first message already contains a job request or property/buyer details. Skipped also if region files are still placeholders — the agent gets the population flow first.

**Why:** v1's pattern required the agent to know what to ask. The 2025 NAR survey identified prompting skill as the friction. The menu makes the available actions discoverable without imposing process on agents who already know what they want.

**Implementation:** referenced by `identity.md § First-turn behavior` and `rules.md`. The menu copy lives entirely in `welcome.md`.

### 4.2 Showing-notes job (new, v2)

**New files:**
- `specialist/reference/checklists/showing-intake.md`
- `specialist/reference/templates/showing-note.md`

**Workflow:**
1. Agent dictates from car after a showing, transcribes via any audio tool, or types a quick summary.
2. Agent pastes into a Claude Project chat with "showing notes job" as the framing.
3. Specialist applies `showing-intake.md`, asks for missing required fields (property, date, buyer, attendees), produces a structured note per `templates/showing-note.md`.
4. Note includes normalized **friction tags** — short kebab-case identifiers (`hoa-cost`, `kitchen-layout`, `flood-risk`).

**Why this isn't just a new job — it's data ingestion.** The note is not a one-shot artifact. Future matching or pricing jobs for the same buyer or property cite the prior note's friction tags. This is the v2 architectural shift: the specialist accumulates context across the agent's week, not just within one conversation.

**Cross-job citation pattern (from the sharpened `frameworks/buyer-fit.md`):**

> "Per the showing note from [date] at [address], buyer flagged `ground-floor-bedrooms` as friction. Listing B has the same configuration — likely a repeat issue."

**Voice discipline preserved.** The note is for the agent. Never addressed to the buyer. Never reformatted into a client-facing email. The discipline holds.

### 4.3 Local-services lookup (new, v2)

**New file:** `specialist/reference/region/services.md` (in the region pack — agent populates).

**Behavior:** When the agent asks "look up an inspector" or "who do we use for jumbo financing?", the specialist retrieves the agent's top pick from `services.md` with reasoning. When a job context surfaces a need ("the pricing memo flags a roof concern"), the specialist proactively offers the relevant vendor.

**Hard rule:** the specialist will *never* invent a vendor. If a category is empty or `[PLACEHOLDER]`, the specialist says so and offers to help populate it. This is non-negotiable — it's the foundation of trust for an agent's own Rolodex.

**Phrasing rule:** the specialist surfaces vendors as the agent's relationships, not as its own recommendations. "From your services list, you've worked with [Name] for [specialty]" — never "I recommend [Name]."

**Date discipline.** Each entry has a `Last updated` field. If older than 12 months, the specialist flags it for verification before passing on.

**Region pack expansion:** the local data folder grew from 5 files to 6. Each of the three case studies (Jerusalem, Novato, Khao Lak) now ships with a populated `services.md` showing the format and the kinds of context-aware notes worth keeping (specialty, language coverage, gotchas).

### 4.4 Sharpened buyer-fit framework

**Edited file:** `specialist/reference/frameworks/buyer-fit.md`.

**What changed:**

1. **Required reasoning chain on the top pick.** The framework now mandates that for the #1 ranked property, the output includes a per-dimension justification (4-line reasoning chain: buyer's preference → property offer → gap → score). This is the difference between a checklist of scores and a recommendation an agent can hand to a client.
2. **"Common shallow miss" column** in the dimensions table — calls out the ChatGPT-style failure modes the framework is designed to avoid (e.g., "counting bedrooms without checking *usable* layout").
3. **"When the data is thin" rule.** If buyer profile or listings are under-specified, the specialist must say so before scoring. Never silently infer.
4. **"When no listing fits" rule.** If no candidate scores above Acceptable on the buyer's heaviest dimensions, the specialist tells the agent explicitly and recommends going back to sourcing.
5. **Citation pattern for prior showing notes** (cross-job memory).
6. **Explicit positioning** as the strongest job vs. raw ChatGPT, with reasoning about why.

**Why this matters.** Per the research, buyer–property fit ranking is the white-space differentiator. Generic ChatGPT can't reach this depth without the same scaffolding behind it. The framework now enforces the depth that makes the output defensible.

### 4.5 "Don't drift" rule

**Edited file:** `specialist/rules.md`.

A new section codifies common drift requests and the redirects:

- "Draft an email to my seller" → CRM territory; redirect to one of the five jobs.
- "Write a blog post / Instagram caption / open-house flyer" → not in scope; suggest a generic AI tool.
- "Cold-email 50 agents in Phoenix" → not in scope; we don't do mass outreach.
- "Predict the market in 2027" → outside the comp-and-reasoning frame; surface what's in `region/market.md` and stop there.
- "Tell me what house to buy myself" → the specialist supports the agent's work for clients, not the agent's personal investing.

The discipline of v1 was implicit. v2 makes it explicit so the specialist redirects predictably.

### 4.6 Expanded "won't do" list

**Edited file:** `specialist/identity.md`.

v1 had three "won't" rules. v2 has five — adding explicit rules against client-facing comms drafts and against inventing vendors not in the agent's services list.

### 4.7 Cross-job memory rule

**Edited file:** `specialist/rules.md`.

A new section explicitly tells the specialist that showing notes are durable input data, and to check the conversation context for prior notes when running matching or pricing jobs for the same buyer or property.

### 4.8 New example (Example 4)

**Edited file:** `specialist/examples.md`.

Added a fourth example: a Novato showing-notes flow with the Hendersons (empty-nester downsizers from Tiburon) at 142 Bel Marin Keys Blvd. Demonstrates dictation-to-structured-note, friction tagging (`kitchen-layout`, `hoa-cost`, `flood-risk`), and the agent-facing follow-up reasoning.

---

## 5. Architecture — Interpretable Context Methodology (ICM)

### What ICM is

A pattern for building "specialist" Claude Projects (or any LLM-with-context-window setup) where:

1. **Folders are architecture.** The directory structure encodes the routing logic. The specialist consults a deterministic subset of files per job type — the structure tells it which.
2. **Files are the program.** Each file has one job. The structure is the documentation.
3. **Universal vs. local separation.** Universal logic lives at one layer (`frameworks/`, `templates/`, `checklists/`, `identity.md`, `rules.md`). Locale-specific data lives in another (`region/`). Switching markets edits exactly one folder.
4. **Templates ARE the output structure.** The file in `templates/` is the literal output shape, not background reference.
5. **Routing table is explicit.** `rules.md` contains a table of jobs → files-to-consult. Token discipline is built in.

### Why this matters beyond real estate

ICM is a candidate pattern for any professional copilot where:

- Output has a few well-defined shapes (templates exist or can be defined).
- Logic has a universal core + a locale or customer-specific overlay.
- The agent needs honest friction-surfacing, not pleasing answers.

Plausible adjacent applications (not implemented): mortgage broker, property manager, commercial real-estate broker, insurance broker, financial advisor. Each shares the "regulated, regional, output-templated" shape that ICM is suited for.

### What ICM is *not*

- Not a no-code agent builder framework.
- Not an MCP server. No live data, no tool calls.
- Not a generalized prompt-engineering library. ICM is opinionated — narrow scope, voice discipline, output templates.

---

## 6. v1 → v2 file diff

### Files added in v2

| File | Lines | Purpose |
|---|---|---|
| `specialist/welcome.md` | ~50 | First-turn menu + welcome flow |
| `specialist/reference/region/services.md` | ~75 | Local vendor KB template |
| `specialist/reference/checklists/showing-intake.md` | ~75 | Showing-notes intake checklist |
| `specialist/reference/templates/showing-note.md` | ~70 | Output structure for showing notes |
| `case-studies/jerusalem/region/services.md` | ~80 | Populated example for Jerusalem |
| `case-studies/novato/region/services.md` | ~95 | Populated example for Novato |
| `case-studies/khao-lak/region/services.md` | ~110 | Populated example for Khao Lak |

### Files edited in v2

| File | Nature of change |
|---|---|
| `specialist/identity.md` | Added 5 jobs (vs. 3); added first-turn behavior pointer; expanded "won't do" from 3 rules to 5. |
| `specialist/rules.md` | Routing table expanded with showing-notes + services rows; "don't drift" section added; cross-job memory section added; templates section expanded. |
| `specialist/examples.md` | Header updated; added Example 4 (showing notes — Novato, Hendersons). |
| `specialist/reference/frameworks/buyer-fit.md` | Substantial rewrite: required reasoning chain, "common shallow miss" column, "when data is thin" rule, "when no listing fits" rule, citation pattern. |
| `specialist/README.md` | File map updated for v2; setup section reflects 6 region files; v1-migration note added. |
| `README.md` (top-level) | Rewritten: 5 jobs, "where it beats raw ChatGPT" section, what's new in v2, v1 pointer. |
| `CONTRIBUTING.md` | Region file count 5 → 6; line count updated. |
| `case-studies/test-results.md` | v2 status note added at top. |

### Files unchanged from v1

- `LICENSE`, `.gitignore`
- All v1 region files in `specialist/reference/region/` *(other than the new `services.md`)*
- All universal frameworks except `buyer-fit.md`
- All checklists except the new `showing-intake.md`
- All templates except the new `showing-note.md`
- All case-study region files for Jerusalem, Novato, Khao Lak *(other than the newly added `services.md`)*

---

## 7. Validation status

### v1 simulated cold-test (six scenarios)

Documented in `case-studies/test-results.md`. Six tests across Jerusalem and Novato (3 each, one per job). The methodology is explicit: outputs are produced by following the loaded files as the specialist would when dropped into a Claude Project. **This is not real-environment validation.**

### v1 real cold-tests

Pending. Two practicing agents lined up: the author's father (Jerusalem) and friend (Marin). Each will drop the deliverable into a fresh Claude Project, populate `reference/region/` from the matching case-study pack, and run real listings/matches/pricings on actual current properties. Findings feed v2.1 calibration.

### v2 cold-test status

The two new jobs (showing notes, services lookup) and the sharpened buyer-fit framework have not yet been cold-tested. v2.1 priority.

A cold-test brief for the two human testers is provided in `docs/cold-test-brief.md`.

---

## 8. Positioning vs. the market

### Where Realtor Copilot beats raw ChatGPT

1. **Buyer–property matching with reasoned friction.** ChatGPT keyword-matches; the specialist reasons about *intensity* of fit, surfaces what the buyer compromises on for the top pick, and tells the agent when none of the candidate listings actually fit.
2. **Price bands with citable comp logic.** Not "list at $X" — a band, with comps the agent can defend on a listing presentation, with adjustment magnitudes pulled from the local market file.
3. **Cross-job memory.** Showing notes captured today can be cited in a matching job next week. Friction tags carry forward.

### Where Realtor Copilot does *not* try to compete

- **Marketing copy** (flyers, IG posts, "just listed" cards) — Listings.ai, Canva, ChatGPT do this. Red ocean.
- **Client-facing comms drafts** — Follow Up Boss, Lofty territory.
- **Mass outreach** — spam-adjacent regardless of quality.
- **Live MLS/comps lookup** — different game; turns the project from no-install to infrastructure-heavy.

### Distribution moat

Free, MIT-licensed, lives in the agent's existing Claude subscription, no API key, no install, no monthly fee. Bypasses the $58–$1,500/month CRM buying cycle that gates Lofty, Follow Up Boss, kvCORE, CINC, etc.

The audience is the 42% of agents already in ChatGPT/Claude weekly who report disappointing impact (NAR 2025) — agents who know they need scaffolding but don't know how to build it.

---

## 9. Roadmap (post-v2)

### v2.1 — validation

- Real cold-tests with the two practicing agents.
- Fold their feedback into universal files (never region files).
- Add real test transcripts to `case-studies/test-results.md`.

### v2.2 — distribution

- Submit to Inman / RISMedia as a free open-source tool.
- Two-minute Loom: agent setup → first listing in 20 minutes.
- One-pager: Realtor Copilot vs. typing into ChatGPT (concrete output diff).
- Third case-study region (Lisbon shipped with v2 if scope allowed; otherwise community contribution).

### v3 — possible expansions (not committed)

- **Comms drafts**, with hardened voice rules. Only if v2.1 cold-tests show the voice rule survives the new surface.
- **Static web onboarding tool** — form-driven setup that produces a populated `specialist.zip`. Removes the markdown-editing barrier for non-technical agents.
- **MCP server for live comps** — wraps Zillow / Redfin / local-MLS APIs. Biggest capability jump, but pulls the project out of "no code, no install" — different game.
- **Sibling specialists** in adjacent professions (mortgage, property management, commercial RE) — validates ICM as a transferable pattern.

---

## 10. Talking points for writers

### Soundbites

- *"A folder of markdown files that turns Claude into a real-estate specialist for your local market — not because it's been trained on your market, but because it reads the files you wrote about it."*
- *"Five jobs only. The copilot redirects everything else — because the moat is what it doesn't try to do."*
- *"Raw ChatGPT keyword-matches. Realtor Copilot reasons about whether the fourth bedroom is functional, what the buyer compromises on for the top pick, and whether none of your candidate listings actually fit."*
- *"42% of agents use AI weekly. Only 17% report significant impact. Realtor Copilot is the structured prompt scaffolding that closes the gap."*
- *"Every paid CRM ships an AI assistant. Realtor Copilot is free, lives in the agent's existing Claude subscription, and ships with three populated case-study markets."*

### Key numbers

| Number | Source |
|---|---|
| 5 jobs in v2 (3 in v1) | Repository |
| 22 specialist files in v2 (17 in v1) | Repository |
| ~3,400 total lines in v2 (~1,400 in v1) | `wc -l` |
| 6 region files per market in v2 (5 in v1) | Repository |
| 3 populated case studies (Jerusalem, Novato, Khao Lak) | Repository |
| 68% of agents use AI; 42% weekly+ | NAR 2025 Technology Survey |
| 17% report significant positive impact | NAR 2025 Technology Survey |
| ChatGPT 58% / Gemini 20% / Copilot 15% share | NAR 2025 Technology Survey |
| Lofty: $499–$1,500/mo | AgentAdvice 2026 |
| CINC: $899+/mo | Industry pricing |
| Realtor Copilot: free | Repository, MIT license |

### Comparison points

| | Realtor Copilot v2 | Lofty / kvCORE / CINC | Raw ChatGPT |
|---|---|---|---|
| Cost | Free (Claude sub only) | $58–$1,500/mo | Free–$20/mo |
| Install | None | Account + setup + onboarding | None |
| Buyer-fit reasoning | Required reasoning chain | Varies; mostly lead-gen focus | Keyword pattern-match |
| Comp-based pricing | Defensible band with logic | CMA tools available, varies | Not reliable |
| Showing notes with cross-job memory | Yes (v2) | Some (Rechat AI Memo) | No |
| Local-services KB | Yes (v2, agent-curated) | CRM contacts, no LLM retrieval | N/A |
| Regional adaptability | One folder edit | Fixed regions or paid expansions | None |
| Honesty rule | Codified | N/A | None |

### Quotables on architecture

- *"Folders are architecture. Files are the program. The structure is the documentation."*
- *"Switching markets edits exactly one folder."*
- *"Templates ARE the output structure — not background reference."*
- *"The discipline is the moat. Five jobs, politely redirect anything else."*

---

## 11. Author / contact

- GitHub: [github.com/NFTYoginis](https://github.com/NFTYoginis)
- Repos: [`realtor-copilot`](https://github.com/NFTYoginis/realtor-copilot) (v1) · [`realtor-copilot-v2`](https://github.com/NFTYoginis/realtor-copilot-v2) (v2)
- License: MIT
- Author background: former real-estate practitioner; built v2 informed by lived agent workflow.

---

*This spec is a living document. v2 status: shipped May 2026. Cold-test calibration pending.*
