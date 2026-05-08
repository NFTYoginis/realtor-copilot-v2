# Realtor Copilot v2 — Press Kit

Title, descriptions, image prompts, and talking points for marketing surfaces (GitHub, Inman/RISMedia submissions, social, agent-facing materials).

---

## Title

**Realtor Copilot** *(primary, evergreen)*

Use the bare project name in repo title, banner, and most marketing. The "v2" designation belongs in version-specific contexts only (changelog, release notes, "what's new").

### Tagline options (pick per surface)

| Surface | Tagline |
|---|---|
| GitHub repo description (current) | Free, no-install AI assistant for residential real-estate agents. Five jobs, no monthly cost beyond Claude. |
| Hero / homepage | **Five jobs. Twenty-minute setup. Free.** |
| Social / one-liner | The structured AI scaffolding that raw ChatGPT doesn't give you. |
| Inman / industry pitch | Free, open-source AI specialist for working agents — listings, comps, buyer fit, showing notes, vendor lookup. |
| Agent-to-agent word-of-mouth | "It's like ChatGPT, but it actually knows my market." |

---

## Descriptions

### Short (≤280 characters — social, repo)

> Free AI assistant for residential real-estate agents. Five jobs — listings, buyer-fit ranking, defensible price bands, showing notes, vendor lookup — tuned to your local market in ~20 minutes. Lives inside Claude. No install, no API key, no monthly fee. MIT.

### Medium (50–80 words — Inman submission, blog intro)

> Realtor Copilot is a free, no-install AI specialist that drops into a Claude Project and handles the five jobs that eat a residential agent's week: writing listings, ranking buyer fit, generating defensible price bands with comps, capturing showing notes, and surfacing vetted local vendors. About 20 minutes to set up for your local market. No API key. No monthly fee beyond your existing Claude subscription. MIT licensed.

### Long (150–200 words — press release, detailed product page)

> Realtor Copilot is an open-source, free AI specialist for residential real-estate agents. Built as a folder of structured markdown files that drops into a Claude Project, it handles five jobs: writing audience-tuned listing descriptions, ranking buyer-property fit with reasoned friction, generating defensible price bands with comp logic, capturing showing notes from dictation or transcript, and surfacing the agent's own curated local vendors.
>
> The architecture is intentionally narrow. It is not a CRM, not a marketing-content generator, and not a mass-outreach tool. It is the structured prompt scaffolding for the agents already typing into ChatGPT or Claude weekly — the cohort the 2025 NAR Technology Survey identified as using AI tools but reporting little impact, citing prompting friction as the gap. By encoding agent-specific reasoning patterns (per-dimension buyer fit, regionally-sourced pricing adjustments, citation-discipline) into the file structure itself, the copilot delivers reasoning quality that raw ChatGPT cannot reach without the same scaffolding behind it.
>
> Setup takes about 20 minutes — fill in six markdown files describing the local market — and the tool runs forever. MIT licensed.

---

## Image prompts (for the design team)

Three concepts. Use the first as the primary hero image; the others are alternates for secondary surfaces.

### Concept 1 — *"Second pair of eyes"* (PRIMARY)

**Subject.** A working real-estate agent at a tidy wooden desk in a sunlit room. Mid-action: looking at a laptop screen, one hand resting near the keyboard, the other holding a paper neighborhood map or a coffee. Calm, focused, not stressed.

**The screen.** The laptop displays a stylized Claude chat interface. Left side: the agent's typed message ("Match my buyer to these 3 listings"). Right side: a structured response with a small ranked-fit table (Listing A / B / C with Clear / Friction / Acceptable visible), a short reasoning paragraph, and a callout box.

**Atmosphere layer.** Around the laptop, faintly translucent: 5–6 floating index cards labeled with the markdown filenames (`market.md`, `neighborhoods.md`, `buyer-fit.md`, `pricing.md`, `showing-note.md`, `services.md`). They feel like the agent's organized second brain, not like floating UI chrome.

**Color palette.** Muted earth tones — warm tan, soft sage, cream, paper-white. One accent color for the ranking table and the file-card edges: deep terracotta or muted teal (designer's choice).

**Style reference.** Editorial illustration in the spirit of *The New York Times* opinion section, *Stripe Press* covers, or *The Atlantic* feature spreads. Flat, slightly textured, clean line work, generous whitespace. Ink + watercolor sensibility, not vector-flat.

**Avoid.**
- Stock-photo "agent shaking client's hand at closing" tropes
- "Sold" signs, suburbs with white picket fences, McMansion exteriors
- AI-cliché imagery: glowing brain, robotic hand, blue tech grid, neural network nodes
- Hyperrealistic 3D renders
- Bright neon gradients or "SaaS purple"
- The agent looking like a tech bro — they should read as a working professional, any age, any presenting gender

**Aspect ratios needed.**
- 1200×630 (Open Graph / GitHub social card)
- 2560×1440 (homepage hero, future site)
- 1080×1080 (Instagram / square)

---

### Concept 2 — *"Five jobs"* (alternate, infographic-style)

A flat-design hero rendered as a horizontal row of five icon tiles, each representing one job. Tile content:

1. **Write a listing** — a stylized "for sale" sign with a paragraph of text emerging from it
2. **Match buyer to listings** — three property cards in a row with a checkmark on one
3. **Price with comps** — a small bar chart with three bars labeled Low / Mid / High
4. **Showing notes** — a microphone icon with a structured bullet list emerging
5. **Vendor lookup** — a Rolodex card with a wrench and a magnifying glass

Header above tiles: **"Five jobs. Twenty-minute setup. Free."** in a generous serif typeface (Playfair, Spectral, or similar).

Color palette: same warm earth tones as Concept 1. One accent for icon highlights.

**Style.** 2D flat illustration with subtle paper texture, soft drop shadows, no gradients, no glow effects. Patagonia field-guide aesthetic — substantive, not flashy.

**Use cases.** Product page sections, social carousel cover, README OG image.

---

### Concept 3 — *"Local market, structured"* (alternate, conceptual)

A single rich illustration: a stylized neighborhood from above, ambiguously generic (could read as Marin, Lisbon, Jerusalem — not too specific). 6–8 city blocks rendered with soft architectural detail, a few key landmarks (a place of worship, a school, a café, a transit stop, a small park).

Overlaid in translucent ink: a folder/file-tree structure showing markdown filenames pinned to relevant parts of the map. `region/neighborhoods.md` pinned to a residential block; `region/market.md` floating over a transaction-active corner; `region/services.md` pinned next to a Rolodex icon by the café.

**Style.** Map-as-illustration in the spirit of *The Atlantic* travel features or hand-drawn editorial maps. Warm earth tones, ink line work, slight watercolor wash.

**Use cases.** "Local market" feature spread, longer-form article hero, deck slide.

**Avoid.** Photorealistic city skylines, tourist-postcard tropes, AI-generated cityscape clichés.

---

## Talking points (for writers and pitches)

Numbers, comparisons, and soundbites worth using. All verifiable from the repo or cited research.

### What it is, in one line

> *"A folder of markdown files that turns Claude into a real-estate specialist for your local market — not because it's been trained on your market, but because it reads the files you wrote about it."*

### The discipline

> *"Five jobs only. The copilot will redirect requests for blog posts, cold outreach, and personal investing — because the moat is what it doesn't try to do."*

### The wedge vs. raw ChatGPT

> *"Raw ChatGPT keyword-matches a 4-bedroom buyer to a 4-bedroom listing. Realtor Copilot reasons about whether the fourth bedroom is functional, what the buyer compromises on for the top pick, and whether none of your candidate listings actually fit."*

### The market context (from NAR 2025 Technology Survey)

> 68% of agents have used AI; 42% use it weekly+. Only 17% report significant positive impact. The friction the survey identifies is *prompting skill + workflow* — exactly the gap structured scaffolding closes.

### The architecture name

> Interpretable Context Methodology (ICM) — folders as architecture, files as the program. The directory structure encodes routing logic; each file has one job; universal logic is separated from local data so switching markets edits one folder.

### v1 → v2, in numbers

| Metric | v1 | v2 |
|---|---|---|
| Specialist files | 17 | 22 |
| Total lines | ~1,400 | ~3,400 (most growth: populated case-study services packs) |
| Jobs | 3 | 5 |
| Region files (per market) | 5 | 6 (added `services.md`) |
| Welcome menu | No | Yes |
| Cross-job memory | No | Yes (showing-note tags carry into matching/pricing) |
| Examples in `examples.md` | 3 | 4 |

### What's NOT in v2 (and why)

- **No marketing-material generator.** Listings.ai, Canva Magic, ChatGPT, and every CRM ship this. Red ocean.
- **No client-facing email drafts.** CRM territory (Follow Up Boss, Lofty). Voice-rule-incompatible.
- **No mass agent-to-agent cold outreach.** Spam-adjacent regardless of copy quality. Walks toward CAN-SPAM and damages reputation.
- **No live MLS / comps API.** Different game — turns the project from no-install to infrastructure-heavy.

### Distribution model — the moat is the cost structure

> *"Every paid CRM ships an AI assistant. The ones we benchmarked run $58–$1,500/month, gated by sales cycles. Realtor Copilot is free, MIT-licensed, lives in the Claude subscription the agent already pays for, and ships with three populated case-study markets that double as setup templates."*

### Validation status (be honest)

- v1's six-test result file is a *simulated* cold-test; the methodology is documented in `case-studies/test-results.md`.
- Real-environment validation with two practicing agents (Jerusalem and Marin County) is the v2.1 priority.
- v2's two new jobs (showing notes, services lookup) have not yet been cold-tested.

---

## Naming the architecture (for the deeper article)

If a writer wants to go deep on the methodology rather than just the product, the angle is:

> *"This isn't a real-estate AI. It's a pattern for any professional copilot — written first as a real-estate tool because the author had domain experience to test it against. The pattern is what scales."*

Adjacent professional copilots that could plausibly use the same structure: mortgage broker, property manager, insurance broker, commercial real-estate broker, financial advisor (for the regulatory caveat / disclosure-sensitive style of work).

---

## License + attribution

MIT. No attribution required, but appreciated. Author: NFTYoginis (GitHub). Encourage forking and contributions — case-study packs for new markets are the most welcome.
