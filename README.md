# Your Market Realtor

**A free AI assistant for residential real-estate agents. Works inside Claude — no install, no API key, no monthly cost beyond your Claude subscription.**

If you already type into ChatGPT or Claude for listings, comps, or buyer notes — and the answers feel generic — Your Market Realtor is the structured prompt scaffolding you've been missing. About 20 minutes to set up for your local market, then it's a chat away.

---

## What it does — five jobs

When you start a new chat, the copilot opens with a menu:

| Job | Ask it... | What you get back |
|---|---|---|
| **Write a listing** | "Write a listing for this 3-bed apartment in [neighborhood]. Audience: international investor." | A finished listing tuned to that buyer pool. Multiple languages on request. |
| **Match a buyer to listings** *(strongest job)* | "Here's my buyer's profile. Here are 4 listings I'm considering showing them. Rank them." | Ranked fit with reasoning, friction points called out, and which one to show first. |
| **Price a property** | "What should this list at? Specs: [...]" | A defensible price band (low / mid / high) with comp set and the reasoning behind every adjustment. |
| **Capture showing notes** *(new in v2)* | "Showing was Saturday. Here's my dictation: [paste]." | A structured note tagged for retrieval. Future matching/pricing jobs cite it back. |
| **Look up a local service** *(new in v2)* | "Who do we use for hillside foundation inspections?" | Your top pick from your own curated services list, with the reasoning. Never invents vendors. |

It won't:

- Give binding legal or tax advice. It surfaces what to ask your lawyer or accountant about.
- Quote a single list price. Always a band with comps.
- Draft client-facing emails (seller updates, buyer follow-ups). That's CRM territory.
- Recommend vendors that aren't in your own services list.
- Try to do anything outside those five jobs.

## Who it's for

Working residential real-estate agents — anywhere in the world. You're the expert in the room. This is your second pair of eyes for the work that takes hours and doesn't really need to.

You don't need to know how to code. You don't need to install anything. If you can use Claude in a web browser, you can use this.

## Where it actually beats raw ChatGPT

Three places. Be honest about the others.

1. **Buyer–property matching with reasoned friction.** ChatGPT keyword-matches ("4BR matches 4BR"). The copilot reasons about *intensity* of fit, surfaces what the buyer will compromise on for the top pick, and tells you when no listing in your candidate set actually works.
2. **Price bands with citable comp logic.** Not "list at $X" — a band, with the comp set you can defend on a listing presentation, with adjustment magnitudes pulled from your local market file.
3. **Cross-job memory.** Showing notes you capture today can be cited in a matching job next week. The friction tags carry forward.

Where ChatGPT is fine: short marketing blurbs, generic Q&A, idea brainstorming. The copilot doesn't try to compete on those — there are dedicated tools and ChatGPT itself does the job. Save the copilot for the work that needs structure.

---

## Setup — step by step (about 20 minutes, one time)

### Step 1 — Download the repo

1. At the top of this page, click the green **"Code"** button.
2. Click **"Download ZIP"**.
3. Find the ZIP file in your Downloads folder and unzip it (double-click on Mac, right-click → Extract All on Windows).

You should now have a folder called `your-market-realtor-main` (or similar) containing `specialist/`, `case-studies/`, `docs/`, and a few other files.

### Step 2 — Open the region folder

Inside the unzipped folder, navigate to:

```
specialist/reference/region/
```

You'll see **six files**, each containing structured prompts and `[PLACEHOLDER]` markers:

- `market.md` — your market overview (inventory, days on market, adjustment magnitudes for pricing)
- `neighborhoods.md` — districts/neighborhoods you work, with anchors and buyer-fit notes
- `regulations.md` — taxes, permits, disclosures, foreign-buyer rules
- `contracts.md` — local contract conventions, transaction stages, common gotchas
- `glossary.md` — local property/legal terms (especially relevant for non-English markets)
- `services.md` — your vetted vendor list (inspectors, lenders, stagers, etc.)

### Step 3 — Fill in the six files for your market

Two paths depending on whether your market resembles one of the case studies:

**Path A — your market is similar to one of the case studies.** Open `case-studies/` and look at the four populated regions (Jerusalem, Novato, Khao Lak, Lisbon). If one is structurally similar to yours, copy the contents of `case-studies/[that-market]/region/` over `specialist/reference/region/` and edit it for your specifics. This is the fastest path.

**Path B — start from scratch.** Open each of the six files in `specialist/reference/region/`. Each one has section headers and `[PLACEHOLDER]` markers showing exactly what to fill in. Replace the placeholders with your local data. Use bullets and tables (the prompts show you how).

A good fill-in is honest and specific:
- "Days on market for renovated 4BR SFH under $1.4M: 14–18 days in Q1 2026" ✓
- "The market is hot" ✗

You don't need to fill every section perfectly. Even partial fills are usable — the copilot will tell you when it's missing something it needs.

### Step 4 — Create a Project in Claude

1. Go to [claude.ai](https://claude.ai) and sign in.
2. In the left sidebar, click **"Projects"**.
3. Click **"New project"** (or "Create project").
4. Name it whatever — *Realtor Copilot* works.
5. Optional: in the project's instructions field, you can leave a short note like "Real-estate copilot for [your market]." Claude will primarily read the files you upload.

### Step 5 — Upload the specialist folder

1. Inside the project, look for **"Project knowledge"** or **"Add to project knowledge"** (Claude has shifted the wording over time — it's the area where you upload reference files).
2. Drag-and-drop your `specialist/` folder into the upload area, OR click "Add" and select all the files inside `specialist/` (including subfolders).
3. Wait for Claude to process the files. You'll see them listed in the project knowledge area when ready.

You should see ~22 files uploaded — the welcome flow, identity, rules, examples, README, and the reference files (region/, frameworks/, checklists/, templates/).

### Step 6 — Start a chat

1. In your project, start a **new chat**.
2. Just say hi or ask a question.
3. The copilot should greet you with the welcome menu — five jobs to choose from.

If the menu doesn't appear, check that all the files in `specialist/` were successfully uploaded to project knowledge. If files are missing, the copilot may not have the welcome flow loaded.

---

## What you'll get — sample outputs

Concrete examples of what each job produces. (See `specialist/examples.md` for full versions.)

### Job 1 — Listing description (Jerusalem, international investor)

You ask:
> Listing job. 4-unit residential building, 5 minutes' walk from Jaffa Gate. ~340 m² total, fully occupied, current monthly rent ~$11,000 USD aggregate. Asking ~$3.4M USD. Audience: Chinese investor, English-speaking intermediary, yield-focused.

You get back:
- An English/investor-framed listing with yield calculation, location thesis, foreign-buyer tax considerations surfaced (Mas Rechisha, Mas Shevach), exit-liquidity note, and a four-step due-diligence checklist.
- A side-by-side Hebrew local-market listing.
- Agent-facing prep notes for the showing — buyer's residency status, source-of-funds path, hold thesis, decision-pace expectations.

### Job 2 — Buyer–property matching (Jerusalem, Modern Orthodox aliyah family)

You ask:
> Matching job. Buyer: Family of 4 relocating from NYC (aliyah). Modern Orthodox; walking-distance shul + day school is critical. Budget $1.5M (stretch $1.65M). Three listings: A) Talbiya 4BR $1.7M walk-up; B) Baka 4BR $1.45M ground-floor garden; C) Old Katamon 3BR + office $1.55M elevator. Rank fit.

You get back:
- A ranked-fit table — Listing C top pick, Listing B at "Friction" with specific reason, Listing A at "Blocker" with specific reason.
- A detailed scoring table for the top pick (Budget / Location / Type-size / Lifestyle / Friction).
- A reasoning chain explaining *why* each score landed where it did.
- An honest tradeoff section ("they asked for 4BR, this is 3+office").
- A "don't dismiss yet" section flagging that Listing B has a real case worth a second showing.

### Job 3 — Pricing band (Novato, Marin County)

You ask:
> Pricing job. 4BR/3BA in Novato (Pleasant Valley), 2,150 sqft, 0.18 acre lot, 1978 single-story, kitchen + primary bath remodeled 2021. Owner targeting on-market within 3 weeks.

You get back:
- A defensible band: **Low $1,225K / Mid $1,275K / High $1,325K**, with when-to-use guidance for each.
- A comp-set table (4 properties, sqft, sale price, $/sqft, sale date, adjustments to subject).
- Adjustment logic with reasoning.
- Market context (days-on-market, season, buyer-pool dependency).
- One short caveat (verify roof condition and 2021 renovation permits).

### Job 4 — Showing notes (Novato, empty-nester downsizers) — *new in v2*

You ask:
> Showing notes job. Showing was 2026-05-04 at 142 Bel Marin Keys Blvd. Buyer: the Hendersons (empty-nesters from Tiburon, $1.5–1.8M). Here's my dictation: [paste]

You get back:
- A structured note with property/buyer header.
- Reaction summary, positive signals, friction (each line marked "from transcript" or "agent's read").
- Comparisons made, questions raised, logistics.
- Agent's read with seriousness rating and homework checklist.
- Friction tags (`kitchen-layout`, `hoa-cost`, `flood-risk`) for retrieval by future matching/pricing jobs.
- Agent-facing notes back ("Linda's kitchen objection is the real obstacle, not the dock — lead the second showing with that").

### Job 5 — Services lookup — *new in v2*

You ask:
> Who's in my services list for inspectors? I have a 1928 stone building in Old Katamon I want pre-listed.

You get back:
- Your top pick by name with reasoning ("From your services list — Mendelson Building Inspections; you've used them on Mandate-era stone buildings; 5–7 day turnaround; reports include Tama 38 readiness assessment").
- A second option if your list has one with relevant specialty.
- A flag if the top pick's `Last updated` is older than 12 months — verify before passing on.

---

## First-run prompts (copy-paste)

Once your region is filled in and uploaded, try one of these:

```
Write a listing for a 3-bedroom apartment in [neighborhood],
[size], [condition]. Audience: international investor.
```

```
I have a buyer: [profile in 1-2 lines]. Here are 3 listings:
[paste listings]. Rank fit.
```

```
What should this list at? [property specs]. I want a band with reasoning.
```

```
Showing notes job. Showing was [date] at [address].
Buyer: [identifier]. Here's my dictation: [paste].
```

```
Who's in my services list for [inspectors / lenders / stagers / etc.]?
```

---

## What's new in v2

| Change | Why |
|---|---|
| **Welcome menu on first turn** | The copilot greets and offers the menu instead of waiting for you to know what to ask. Skipped automatically if your first message is already a job request. |
| **Showing-notes job** | Audio-to-structured-note isn't a one-shot artifact — the notes become citable inputs for future matching and pricing jobs for the same buyer or property. |
| **Local-services lookup** | Your vendor list lives in `region/services.md`. The copilot retrieves your top pick with reasoning. It will never invent a vendor. |
| **Sharpened buyer-fit reasoning** | The framework now requires per-dimension justification on the top pick — closing the gap between "checklist of scores" and "reasoned recommendation an agent can hand a client." |
| **"Don't drift" rule** | Explicit boundary: the copilot supports five jobs, redirects everything else (cold outreach, blog posts, market predictions, personal investing). |
| **New case study: Lisbon** | Adds a mainstream urban European international-buyer market alongside Jerusalem (diaspora-driven), Novato (universal-no-foreign-hook), and Khao Lak (resort/foreign-dominant). |

Migrating from v1? Drop your existing `region/` files into the v2 `specialist/reference/region/` directory, then add a `services.md` for your vendor list. Everything else upgrades cleanly.

---

## Already populated for these markets

The `case-studies/` folder contains four populated regions you can use as-is or as a starting template:

| Market | Notable traits |
|---|---|
| **Jerusalem, Israel** | Multi-language (Hebrew + English), strong international diaspora flow, complex title types (Tabu vs. Khevra Meshakenet). |
| **Novato / Marin County, CA** | English-monolingual U.S. suburban market — proves the architecture works without any foreign-buyer dependency. |
| **Khao Lak, Thailand** | Coastal resort, foreign-buyer-dominant, leasehold/freehold structure, multi-language (English / German / Russian / Mandarin). |
| **Lisbon, Portugal** *(new in v2)* | Mainstream urban European international-buyer market, post-Golden-Visa context, multilingual (Portuguese / English / French / Brazilian Portuguese), Roman-law title system. |

Each pack now includes a populated `services.md` showing the format and the kinds of context-aware notes worth keeping.

To use one as-is: copy the contents of `case-studies/[market]/region/` over `specialist/reference/region/`, then upload the `specialist/` folder to your Claude Project.

---

## FAQ / Troubleshooting

### The copilot didn't greet me with the menu when I started a chat.

Most likely the welcome file didn't get loaded into project knowledge. Open your Claude Project, check that `specialist/welcome.md` is in the project files. If it's not, re-upload the `specialist/` folder. If it is, paste this into the chat:

```
Show me the welcome menu from welcome.md.
```

If the copilot still doesn't produce the menu, check that all of `identity.md`, `rules.md`, and `welcome.md` are in project knowledge.

### The copilot keeps saying my region files have placeholders.

That's the empty-region detection working as intended. Open the file(s) it flagged in `specialist/reference/region/` and replace the `[PLACEHOLDER]` text with your actual data. You don't have to fill every section — partial fills are fine — but the copilot will tell you when it can't do substantive work without the data it needs.

### Can I use this with ChatGPT instead of Claude?

The architecture should work with any large-context LLM that supports a project / file knowledge base. We've designed and tested it against Claude Projects. Adapting to ChatGPT Custom GPTs or another platform may require some rewording of the file-routing instructions in `rules.md`.

### Can I use this for commercial real estate / rentals / property management?

The specialist's scope is **residential sales and rentals**. Occasional commercial deals where they touch your residential book are within scope (per `identity.md`), but a dedicated commercial workflow is out of scope. If you want a commercial-focused specialist, the architecture pattern (ICM) transfers — fork and rebuild the framework files for commercial.

### My output sometimes has factual errors about my market.

The copilot only knows what's in your `region/` files plus general background knowledge. If it's making errors, your `region/` files probably need more specifics in the relevant area. Add them and re-upload. The fix is in the data, not the code.

### Can I share my populated region pack publicly?

Yes — and you're encouraged to. See `CONTRIBUTING.md`. Publishing a populated region pack as a case study helps the next agent in your geography get started fast. Don't share your real `services.md` publicly though — those are your relationships.

### How do I update when v2.x or v3 ships?

Re-download the repo. Replace the universal files (everything in `specialist/` *except* the `reference/region/` folder). Keep your populated `region/` folder. Re-upload to your Claude Project.

### Does this cost anything?

No. It's MIT-licensed and free. The only cost is your existing Claude subscription (Claude has a free tier; Pro is $20/month if you need higher usage).

### What's the difference between v1 and v2?

v1 is at [github.com/NFTYoginis/realtor-copilot](https://github.com/NFTYoginis/realtor-copilot). It has three jobs (listing, matching, pricing) and three case studies. v2 (this repo) adds two jobs (showing notes, services lookup), the welcome menu, sharpened buyer-fit reasoning, the "don't drift" rule, and a fourth case study (Lisbon). v2 is a clean superset — migrate by copying your v1 region files plus adding a `services.md`.

---

## Adding your market as a new example

If you populate this for a new market and want to share it back so the next agent in your geography has a head start, see `CONTRIBUTING.md`. New region case studies are the most welcome contribution.

## How this is built

Plain markdown files in folders. No code, no install, no API keys, no monthly cost beyond your existing Claude subscription. Each file has one job; the structure is the documentation.

The architecture is called **Interpretable Context Methodology (ICM)** — folders as architecture, files as the program. If you're a developer or curious about the mechanics, the routing logic in `specialist/rules.md` and the framework files in `specialist/reference/frameworks/` show how each request gets only the files it needs.

For a deep technical walkthrough, see [`docs/v1-to-v2-spec.md`](docs/v1-to-v2-spec.md).

## Documentation

- [`docs/v1-to-v2-spec.md`](docs/v1-to-v2-spec.md) — full architectural spec and v1→v2 changelog
- [`docs/press-kit.md`](docs/press-kit.md) — title, descriptions, image prompts, talking points
- [`docs/cold-test-brief.md`](docs/cold-test-brief.md) — for practicing agents running validation
- [`docs/media-outreach-kit.md`](docs/media-outreach-kit.md) — pitches and press materials

## v1

v1 lives at [github.com/NFTYoginis/realtor-copilot](https://github.com/NFTYoginis/realtor-copilot) — three jobs, no welcome menu, no services lookup, no showing notes. v2 is a clean superset.

## License

MIT — see `LICENSE`. Free to use, modify, share, and sell what you build with it.
