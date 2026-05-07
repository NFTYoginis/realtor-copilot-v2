# Realtor Copilot v2

**A free AI assistant for residential real-estate agents. Works inside Claude — no install, no API key, no monthly cost beyond your Claude subscription.**

If you already type into ChatGPT or Claude for listings, comps, or buyer notes — and the answers feel generic — Realtor Copilot is the structured prompt scaffolding you've been missing. About 20 minutes to set up for your local market, then it's a chat away.

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

## Setup (about 20 minutes, one time)

1. **Download this repo.** Click the green "Code" button at the top → Download ZIP. Unzip it.
2. **Open the `specialist/reference/region/` folder.** You'll see six files with placeholders.
3. **Fill them in for your market.** Market overview, regulations, neighborhoods, contracts, glossary, and your services list. Each file has structured prompts. If your market is similar to one of the examples in `case-studies/`, copy that pack as a starting point and edit.
4. **Create a Project in Claude.** Go to claude.ai → Projects → New Project. Upload the entire `specialist/` folder.
5. **Start a chat in that Project.** Say hi. The copilot opens with the menu.

## First-run prompts (copy-paste)

Once your region is filled in, try one of these:

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

## What's new in v2

| Change | Why |
|---|---|
| **Welcome menu on first turn** | The copilot greets and offers the menu instead of waiting for you to know what to ask. Skipped automatically if your first message is already a job request. |
| **Showing-notes job** | Audio-to-structured-note isn't a one-shot artifact — the notes become citable inputs for future matching and pricing jobs for the same buyer or property. |
| **Local-services lookup** | Your vendor list lives in `region/services.md`. The copilot retrieves your top pick with reasoning. It will never invent a vendor. |
| **Sharpened buyer-fit reasoning** | The framework now requires per-dimension justification on the top pick — closing the gap between "checklist of scores" and "reasoned recommendation an agent can hand a client." |
| **"Don't drift" rule** | Explicit boundary: the copilot supports five jobs, redirects everything else (cold outreach, blog posts, market predictions, personal investing). |

Migrating from v1? Drop your existing `region/` files into the v2 `specialist/reference/region/` directory, then add a `services.md` for your vendor list. Everything else upgrades cleanly.

## Already populated for these markets

The `case-studies/` folder contains three populated regions you can use as-is or as a starting template:

| Market | Notable traits |
|---|---|
| **Jerusalem, Israel** | Multi-language (Hebrew + English), strong international diaspora flow, complex title types (Tabu vs. Khevra Meshakenet). |
| **Novato / Marin County, CA** | English-monolingual U.S. suburban market — proves the architecture works without any foreign-buyer dependency. |
| **Khao Lak, Thailand** | Coastal resort, foreign-buyer-dominant, leasehold/freehold structure, multi-language (English / German / Russian / Mandarin). |

Each pack now includes a populated `services.md` showing the format and the kinds of context-aware notes worth keeping.

To use one as-is: copy the contents of `case-studies/[market]/region/` over `specialist/reference/region/`, then upload the `specialist/` folder to your Claude Project.

## Adding your market as a new example

If you populate this for a new market and want to share it back so the next agent in your geography has a head start, see `CONTRIBUTING.md`. New region case studies are the most welcome contribution.

## How this is built

Plain markdown files in folders. No code, no install, no API keys, no monthly cost beyond your existing Claude subscription. Each file has one job; the structure is the documentation.

The architecture is called **Interpretable Context Methodology (ICM)** — folders as architecture, files as the program. If you're a developer or curious about the mechanics, the routing logic in `specialist/rules.md` and the framework files in `specialist/reference/frameworks/` show how each request gets only the files it needs.

## v1

v1 lives at [github.com/NFTYoginis/realtor-copilot](https://github.com/NFTYoginis/realtor-copilot) — three jobs, no welcome menu, no services lookup, no showing notes. v2 is a clean superset.

## License

MIT — see `LICENSE`. Free to use, modify, share, and sell what you build with it.
