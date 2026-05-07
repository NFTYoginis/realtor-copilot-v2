# Realtor Copilot — Specialist Folder (v2)

**Drop this folder (`specialist/`) into a Claude Project. Fill in the 6 region files for your local market. Start a chat — the copilot opens with a menu.**

## What it does — five jobs

| Job | Ask Claude... | What you get back |
|---|---|---|
| **Write a listing** | "Write a listing for [property]. Audience: [local / English-speaking / international investor]." | A finished listing tuned to that buyer pool. Multiple languages on request. |
| **Match a buyer to listings** *(strongest job)* | "Here's a buyer profile and N listings. Rank fit." | Ranked fit with reasoning, friction points called out, and which one to show first. |
| **Price a property** | "What should this list at? Specs: [...]" | A defensible price band (low / mid / high) with comp set and reasoning. |
| **Capture showing notes** *(v2)* | "Showing was [date]. Here's my dictation: [...]" | A structured note tagged for retrieval — cited later by matching/pricing jobs. |
| **Look up a local service** *(v2)* | "Who's in my services list for [inspector / lender / stager / etc.]?" | Your top pick with reasoning. Will not invent vendors. |

## What it won't do

- Give binding legal or tax advice. It surfaces what to ask your lawyer or accountant.
- Quote a single list price. Always a band with comp logic.
- Draft client-facing emails or peer cold-outreach. CRM territory.
- Recommend vendors not in your own `region/services.md`.
- Try to do anything outside the five jobs above. It will politely redirect.

## Setup (about 20 minutes, one time)

1. Open the `reference/region/` folder. You'll see six files with `[PLACEHOLDER]` markers.
2. Fill them in for your market: market overview, regulations, neighborhoods, contracts, glossary, **and your services list** (new in v2). Each file has structured prompts. If your market resembles one of the examples in `../case-studies/`, copy that pack as a starting point and edit.
3. Drop this entire `specialist/` folder into your Claude Project's knowledge.
4. Start a chat in that Project. The specialist opens with the welcome menu.

## First-run prompts (copy-paste)

Once `reference/region/` is populated, try one of these:

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

## File map

```
specialist/
├── welcome.md          ← first-turn menu (v2)
├── identity.md         ← who Claude becomes
├── rules.md            ← how Claude responds; routing logic per job
├── examples.md         ← four example interactions, one per major job
├── reference/
│   ├── region/         ← YOUR LOCAL MARKET (6 files — you fill these in)
│   │   ├── market.md
│   │   ├── neighborhoods.md
│   │   ├── regulations.md
│   │   ├── contracts.md
│   │   ├── glossary.md
│   │   └── services.md        ← your vendor list (v2)
│   ├── frameworks/     ← universal logic (pricing, buyer-fit, intl-buyers)
│   ├── checklists/     ← structured intake (listing, buyer, showing-v2)
│   └── templates/      ← output scaffolds (listing, fit-summary, pricing, showing-v2)
└── README.md           ← this file
```

## Switching markets later

Edit the 6 files in `reference/region/`. That's the only place market-specific data lives — everything else stays the same.

## Migrating from v1

If you already had v1 region files populated:

1. Copy your existing five `region/*.md` files into `reference/region/`.
2. Add a new `services.md` (template provided in this folder, or copy a populated one from `../case-studies/`).
3. That's it. The universal files (identity, rules, examples, frameworks, templates) are upgraded versions — drop them in as-is.
