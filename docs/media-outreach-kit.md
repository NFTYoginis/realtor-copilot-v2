# Media Outreach Kit — Realtor Copilot v2

Materials for submitting Realtor Copilot to industry press (Inman, RISMedia, HousingWire, Real Estate News, The Real Deal) and adjacent outlets (Hacker News, Product Hunt, indie-tools newsletters). Pitches are copy-ready; adjust the byline and contact line before sending.

This is *outreach material* — actual outreach is human-sent (you'll need a real email address, byline, follow-through). The author handles sending; this kit removes the writing step.

---

## Pitch email — Inman

**Subject lines (pick one):**
- A free, open-source AI specialist for residential agents — built by a former practitioner
- The 42% of agents using AI weekly aren't getting impact. Here's the structured prompt scaffolding they're missing.
- Realtor Copilot v2 — five jobs, no install, MIT licensed

**Body:**

> Hi [editor name],
>
> I'm a former residential real-estate practitioner who shipped an open-source AI tool for working agents this month. I'd like to pitch it to Inman — not for promotional coverage, but because it engages directly with a finding from your own reporting and the 2025 NAR Technology Survey.
>
> NAR's data: 68% of agents have used AI; 42% weekly. Only 17% report significant positive impact. The friction Inman has covered in detail — prompting skill, no integrated workflow, "agent vs. algorithm" credibility pressure — is exactly the gap the tool addresses.
>
> **What it is.** Realtor Copilot is a folder of structured markdown files that drops into a Claude Project. About 20 minutes to fill in six files describing your local market. The copilot then handles five jobs:
>
> - Listing descriptions (audience-tuned, bilingual where needed)
> - Buyer–property fit ranking with reasoned friction
> - Pricing memos with defensible comp bands
> - Showing notes from dictation (with cross-job memory — notes from this week cite into matching/pricing next week)
> - Local-services lookup from the agent's own curated vendor list
>
> Free. No install. No API key. No monthly fee beyond the agent's existing Claude subscription. MIT licensed. Three populated case-study markets ship with it: Jerusalem, Novato/Marin, Khao Lak — proves portability across very different regions.
>
> **The wedge isn't features — it's the cost structure and the discipline.** Every paid CRM ($58–$1,500/mo) bundles an AI assistant. The audience here is the agent who's already typing into ChatGPT or Claude, knows it's not landing, and doesn't want to add a $500/month CRM line item to fix it.
>
> If you'd like a closer look, the repos are public:
>
> - v2: https://github.com/NFTYoginis/your-market-realtor
> - v1: https://github.com/NFTYoginis/realtor-copilot
>
> Happy to send a 2-minute walkthrough or get on a call if it's relevant for the next AI-in-real-estate piece.
>
> Best,
> [Your name]
> [Email] · [Phone if you want it]

---

## Pitch email — RISMedia

**Subject lines:**
- Open-source AI for working agents — free, no install, ships with three populated regions
- Realtor Copilot v2: structured prompt scaffolding for the agents using ChatGPT but not getting impact

**Body:**

> Hi [editor name],
>
> Following RISMedia's coverage of "Real Estate's AI Hype: Where It Gets It Right and Wrong" — I'd like to share an open-source tool that engages with the gap your piece described. It's free, MIT-licensed, and built by a former residential practitioner.
>
> **Realtor Copilot** is a folder of markdown files that turns a Claude Project into a specialist for the agent's local market. Five jobs: listings, buyer-fit ranking, pricing with comps, showing notes (new in v2), local-services lookup (new in v2). Setup is about 20 minutes. There's no API key, no install, and no monthly cost beyond the agent's existing Claude subscription.
>
> The architecture is intentionally narrow. The copilot will not write blog posts, draft client-facing emails, or run mass cold outreach — discipline is the moat. The wedge against raw ChatGPT is buyer–property fit ranking with reasoned friction (white space, per market research) and pricing memos with defensible comp logic.
>
> Three populated case-study markets ship with v2: Jerusalem (international-buyer wedge, bilingual), Novato/Marin County (universal-logic-without-foreign-hook proof), and Khao Lak (resort, leasehold/freehold, multi-language).
>
> Repo: https://github.com/NFTYoginis/your-market-realtor
>
> If a free-tools roundup, an open-source spotlight, or an "AI for solo agents" piece is in the pipeline, this is a clean fit. Happy to send a walkthrough or a 1-pager.
>
> Best,
> [Your name]

---

## Pitch email — HousingWire / Real Estate News / The Real Deal

Use the RISMedia template above with the outlet name swapped, plus this addition for outlets that lean more business/financial than agent-facing:

> Distribution model is worth a note: every paid AI-bundled CRM (Lofty, kvCORE, CINC, Follow Up Boss, Top Producer, Rechat) prices in the $58–$1,500/month range. Realtor Copilot is free. The structural argument is that the AI scaffolding agents need does not need to be paywalled into a CRM stack — most of the value is in the prompt structure, not the data integration.

---

## Press release (long-form)

For wire services, blog syndication, or as a one-pager for cold introductions.

---

**FOR IMMEDIATE RELEASE**

# Realtor Copilot v2 Ships — Free, Open-Source AI Specialist for Residential Real-Estate Agents

**Author:** NFTYoginis · **Date:** May 2026 · **License:** MIT

A former residential real-estate practitioner has released Realtor Copilot v2, an open-source AI specialist for working agents. The tool ships as a folder of structured markdown files that drops into a Claude Project; about 20 minutes of setup tunes it to a local market. It handles five jobs — listing descriptions, buyer-property fit ranking, pricing with comps, showing notes from dictation, and local-services lookup — and is free to use, modify, and redistribute.

**Targeting the gap NAR's research identified.** The 2025 NAR Technology Survey found that 42% of agents use AI tools weekly, but only 17% report significant positive impact. The friction the survey identified — prompting skill and workflow integration — is the gap Realtor Copilot directly addresses. Rather than asking agents to generate better prompts, the copilot encodes the structure into its file architecture: each job routes to a specific subset of files, output follows defined templates, and the copilot redirects requests outside its five-job scope.

**Three populated case-study markets ship with the tool.** Jerusalem (Israel) demonstrates the international-buyer wedge with multilingual output and complex title-type handling. Novato/Marin County (California) demonstrates that the universal logic works without any foreign-buyer dependency — Mello-Roos disclosure handling, Bay Area outflow buyer dynamics. Khao Lak (Thailand) demonstrates resort/foreign-buyer-dominant markets with leasehold/freehold structures and four-language coverage.

**The wedge against raw ChatGPT is buyer-property matching with reasoned friction and pricing memos with defensible comp logic** — both white-space areas in the competitive landscape. Bundled AI in CRMs (Lofty, kvCORE, CINC, Follow Up Boss) is priced in the $58–$1,500/month range; Realtor Copilot is free, lives in the agent's existing Claude subscription, and requires no installation, API key, or recurring fee.

**v2 adds two new jobs and cross-job memory.** The showing-notes job converts agent dictation or transcripts into structured notes with normalized friction tags. Future matching or pricing jobs for the same buyer or property cite those tags as input data. The local-services lookup retrieves vendors from the agent's own curated list — never invents — and flags entries older than 12 months for verification.

**The architecture is called Interpretable Context Methodology (ICM)** — folders as architecture, files as the program. Universal logic is separated from local market data, so switching markets edits exactly one folder. The pattern is designed to be portable across professional copilots: mortgage broker, property manager, insurance broker, and adjacent fields share the structural shape ICM is suited for.

**v1 shipped earlier this month** with three jobs (listing, matching, pricing) and three case studies. v2 is a clean superset; v1 region files migrate to v2 by adding a sixth file (`services.md`) for the agent's vendor list.

**Validation:** v1's six-test result file is documented as a *simulated* cold-test. Real-environment validation by two practicing agents (Jerusalem and Marin County) is the v2.1 priority and will be folded into universal files post-test.

**Repos.** v2: github.com/NFTYoginis/your-market-realtor · v1: github.com/NFTYoginis/realtor-copilot

**License.** MIT — free to use, modify, share, and sell what you build with it.

**Contact.** [Author email] · [Author handle]

---

## Hacker News submission

**Title (HN-style — under 80 chars, no marketing language):**

> Show HN: Realtor Copilot v2 – markdown files that turn Claude into a real-estate specialist

**First-comment context (HN convention — author posts a brief context comment immediately):**

> Author here. I worked in residential real estate before building this. v1 shipped earlier this month with three jobs (listing copy, buyer-property fit ranking, pricing memos with comps); v2 expands to five and adds cross-job memory via a showing-notes flow.
>
> The architecture is intentionally narrow — folder of markdown files, no install, no API key, drops into a Claude Project. About 20 min to fill in six files describing your local market. Three populated case-study markets ship with it (Jerusalem, Novato/Marin, Khao Lak) so you can see the format and use them as templates.
>
> The discipline is the moat. The copilot will redirect requests for marketing flyers, client-facing email drafts, or mass cold outreach. It supports five jobs only.
>
> Calling out the architecture pattern (Interpretable Context Methodology — folders as architecture) because I think it's portable to other professional copilots beyond real estate. Happy to discuss in comments.

---

## Product Hunt launch (later — after v2.1 cold-tests)

Suggest waiting on Product Hunt until real cold-test transcripts exist, since PH expects polished case studies and Realtor Copilot's strength is real-world validation, not feature breadth. After v2.1 ships with real-agent transcripts in the test-results file, this is a strong PH submission.

**PH tagline (when ready):**

> Free AI specialist for real-estate agents. Five jobs in 20 minutes. Lives in Claude.

---

## Indie-tools newsletters (post-v2.1)

Worth pitching after real-agent validation lands:

- **Indie Hackers** — open-source / free-tool angle.
- **Hacker Newsletter** — weekly digest of HN's best.
- **Console.dev** — developer-tools weekly (architectural angle: ICM as a pattern).
- **TLDR** — tech newsletter, fits as an "interesting open-source weekend project" item.
- **Real-estate-specific newsletters** — The Lazy Agent, BAM, The CE Shop blog, RealTrends.

Pitch template for newsletters:

> Hi [name],
>
> Quick note in case it's a fit for [newsletter name]. I shipped a free, open-source AI specialist for residential real-estate agents — markdown files that drop into Claude, no install, five jobs, ~20 min setup. Built by a former practitioner. v2 just shipped at github.com/NFTYoginis/your-market-realtor.
>
> If you cover free agent tools, ChatGPT-as-workflow tools, or open-source weekend projects, happy to send a 1-pager.
>
> Best,
> [Name]

---

## What NOT to do

- **Don't pay for placement.** Sponsored coverage will associate the project with a sales-y posture that contradicts the "discipline is the moat" framing.
- **Don't pitch before real-agent cold-tests.** The honest framing requires the simulated-test caveat, and editors will ask. Better to have *real* findings to point to.
- **Don't volume-pitch.** Five well-targeted outlets is better than fifty form-letter pitches.
- **Don't soften the discipline in the pitch.** The "we don't do marketing copy / mass outreach / personal investing" stance is a feature, not a limitation. Editors find that interesting.

---

## Tracking

Suggest a single google sheet or markdown file for outreach tracking:

| Outlet | Contact | Date sent | Response | Outcome |
|---|---|---|---|---|
| Inman | [editor] | — | — | — |
| RISMedia | [editor] | — | — | — |
| HousingWire | [editor] | — | — | — |
| HN | self | — | — | — |
| The Lazy Agent | [editor] | — | — | — |

---

*This kit ships materials only. Outreach itself is the human's job — you'll need a real byline, contact line, and follow-through.*
