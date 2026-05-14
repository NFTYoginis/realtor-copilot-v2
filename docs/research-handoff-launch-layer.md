# Research handoff — Voiceprint launch-layer pattern + Realtor Copilot v2 assessment

**Source:** research-claude (`~/Desktop/Claude Research Assistant/`), dispatched 2026-05-12
**Author class:** utility-only external researcher. **Findings only — not a build plan.** Implementation decisions, sequencing, worker dispatches, and architectural choices are this project's call, not the researcher's.

## What this doc carries

Three research-claude reports informed this handoff. If you want the full derivation, read them in order:

1. [`~/Desktop/Claude Research Assistant/reports/2026-05-12-skool-comp-three-standouts.md`](file:///Users/gabe/Desktop/Claude%20Research%20Assistant/reports/2026-05-12-skool-comp-three-standouts.md) — pattern scout of 3 standout repos from the Skool competition (Voiceprint / AreWeOK / Grief Admin Compass); 5 named patterns extracted.
2. [`~/Desktop/Claude Research Assistant/reports/2026-05-12-voiceprint-launch-layer-jdm-application.md`](file:///Users/gabe/Desktop/Claude%20Research%20Assistant/reports/2026-05-12-voiceprint-launch-layer-jdm-application.md) — the launch-layer pattern + JDM mapping (superseded; kept on file with supersession note + meta-builder addendum at bottom).
3. [`~/Desktop/Claude Research Assistant/reports/2026-05-12-voiceprint-launch-layer-your-market-realtor.md`](file:///Users/gabe/Desktop/Claude%20Research%20Assistant/reports/2026-05-12-voiceprint-launch-layer-your-market-realtor.md) — the live target: Realtor Copilot v2 assessed against the Voiceprint launch-layer pattern.

---

## The Voiceprint pattern in one paragraph

Ruben Aguirre won the Skool competition not because the repo (`github.com/8signal/voiceprint`, MIT) was best — by his own admission others were technically better — but because he shipped **six artifacts together** that work at different funnel stages: (1) **public sales page** at `voiceprint.8signal.com` doing cold→curious; (2) **browser intake wizard** at the same domain (TypeScript site, 20 questions → user downloads their populated `identity.md`) doing curious→user-with-artifact; (3) **six published LinkedIn posts in his own voice** with engagement metrics (47/38/54/21/29/18 reactions) doing skeptic→believer; (4) **video demo** embedded on sales page doing skim-readers→informed; (5) **paid Done-with-You Playbook tier** (8 modules) doing user→buyer; (6) **submission framing** addressing the obvious counter-argument head-on. None substitute for the others. Ship them together or the chain breaks.

## Voiceprint deeper-read findings (quotables for reference)

These are the specific bits the research surfaced that may be worth quoting verbatim or modeling against:

- **Rule 0 (the refusal gate), exact wording from `8signal/voiceprint/rules.md`:** *"If the user asks for content without providing source material, a transcript, a V/TO entry, a weekly review, a client win, a real conversation, ask for one. Do not invent."* Refusal escalation language: *"I don't write from blank pages. Tell me what actually happened this week and I'll turn it into a post."*
- **Identity-template structure (11 sections):** Who you are / Who you serve / What you actually do / Voice in one sentence / Voice pillars (3-5 named traits, each with "sounds like" + "does NOT sound like" contrasts) / Vocabulary (real phrases + AI-cousin phrases + banned terms) / Content themes / Source artifacts checklist / Hashtag strategy / Sign-off / Voice check.
- **Examples.md proof mechanism:** runs the *same source artifact* through Maya / Ruben / Dale identities to produce audibly different outputs. The comparison IS the proof of voice preservation — not a separate testimonial about it.
- **Rule 13 — early-stage calibration:** sessions 1-3 require a mandatory 5-question feedback gate (voice match 1-5, closest/furthest lines, banned phrases, biggest change); results append to `feedback-log.md` and immediately update `identity.md`. Self-correcting loop on actual user reactions.
- **Reference folder (L4) holds dense knowledge** not always-loaded: `identity-examples/`, `intake-interview.md`, `post-formats.md`, `source-protocols.md`.

## Realtor Copilot v2 assessed against the pattern

**Headline finding:** Realtor Copilot v2 is **already ~60-70% built** on the Voiceprint launch-layer pattern, and on several dimensions exceeds Voiceprint:

| Voiceprint piece | Realtor Copilot v2 status |
| --- | --- |
| Specialist core (identity / rules / examples / reference) | **Done, exceeded.** 5 jobs vs Voiceprint's 1; routing-table token discipline in `specialist/rules.md`; "don't drift" rule; empty-region handling. |
| Identity examples (Maya/Dale/Sarah equivalent) | **Done, exceeded.** 4 populated case studies (Jerusalem / Novato / Khao Lak / Lisbon) vs Voiceprint's 3 cold identity examples. |
| Press / outreach materials | **Done, exceeded.** `docs/press-kit.md` + `docs/media-outreach-kit.md` + `docs/outreach-top-5.md`/`html` (described in git as "paste-and-send package") + `docs/cold-test-brief.md`. Voiceprint has none visible. |
| Objection-handling | **Done.** README FAQ section. |
| Open-source community shape | **Done.** MIT + `CONTRIBUTING.md` + live public mirror at `github.com/NFTYoginis/your-market-realtor`. |
| Versioning + clean-superset story | **Done.** `docs/v1-to-v2-spec.md` (27KB); README "What's new in v2" rationale table. |

**Three named gaps:**

1. **Standalone sales surface separate from the 18.5KB `README.md`** — the README is currently doing sales-page + user manual + FAQ in one file. That works for free MIT, but starts to fray when outreach emails / press / ads need to link to a focused sales page.
2. **Real-agent receipts** — the 4 case studies are *cold* examples (operator-populated proof the architecture works). Voiceprint's 6 in-his-own-voice LinkedIn posts were *warm* receipts (real use, real response). Currently missing.
3. **Demo video** — none visible in `docs/`, none referenced in README. Voiceprint embeds a video on the sales page to compress "what does this look like in practice" for skim-readers.

**Skipped (architectural-choice finding, not a gap):** the case-study-pack-as-starter path (Path A in README) is a deliberate substitute for Voiceprint's browser intake wizard — and is *better* than a wizard for this domain (faster, more concrete, no friction-of-misdescription). Don't build a local wizard. The Option-C paid hosted layer (below) is a different thing — that's a SaaS-ifying of the entire copilot, not a wizard for region-pack intake.

## Operator decision recorded

**2026-05-12 — operator selected Option C:** free open-source tool + paid hosted SaaS wizard ($10-30/mo range). The two alternatives considered (A: stay 100% free; B: free tool + paid setup service for region-pack population) were not chosen.

## Voiceprint sales-page architecture (pattern detail)

Deeper read of `voiceprint.8signal.com` + `voiceprint.8signal.com/playbook` 2026-05-12 in response to the operator's question "how will it build a sales page like the winner?" Patterns observed, not prescriptions. The realtor project decides which to apply, which to adapt, what to skip, what new patterns to invent.

### The free-tool sales page (`voiceprint.8signal.com`)

**Section sequence top-to-bottom (21 sections, single-column long scroller):**

1. Nav bar (logo + 4 links: See it work / Done with you / GitHub / Build my identity)
2. Hero: headline + sub-headline + 2 CTAs
3. "The fastest path · Recommended" — intro + transcript pitch
4. "Drop transcripts. Skip the questionnaire." — feature explanation
5. "It already works" — social proof headline
6. "Six posts in three days." — case study intro
7. **6 embedded LinkedIn posts** (the proof block)
8. "What makes it different" — differentiation
9. "Why it sounds like you" — mechanism explanation
10. Three subsections (Identity / Rules / Examples)
11. "The voice gets sharper every week" — process explanation
12. "Read / Pattern / Approve" — three-step workflow
13. "How you use it" — three-step onboarding
14. "01 Build your identity"
15. "02 Drop in an artifact"
16. "03 Get posts in your voice"
17. "Ready to build your voice?" — primary CTA section
18. "For developers and ICM judges" — dev section heading
19. "Under the hood: a folder." — technical architecture
20. Code block showing the repo folder structure
21. Footer

**Verbatim above-the-fold copy:**
- Headline: *"Your voice on LinkedIn. Not a copywriter's."*
- Sub-headline: *"A 30-minute meeting becomes a LinkedIn post you'd actually want to post. In your voice. Not the AI version of you."*
- Tagline: *"For subject matter experts who already have a voice"*

**Patterns observed (free-tool sales page):**

| # | Pattern | Detail |
| - | --- | --- |
| 1 | **Text-only hero, no product mockup** | No image, video, screenshot, or device frame above the fold. The value-prop copy carries the weight alone. Voiceprint deliberately doesn't show a screenshot of a finished LinkedIn post in the hero — the proof block does that work, lower on the page. |
| 2 | **Real embeds as proof, not screenshots** | The 6 LinkedIn posts are full live LinkedIn iframes — author name + title + timestamp + post text + engagement metrics (47 / 38 / 54 / 21 / 29 / 18 reactions) + Like/Comment/Repost/Send buttons. Reader sees the post as it appears on LinkedIn, with real numbers, not a curated screenshot the reader has to trust. |
| 3 | **Objection-handling woven into features, no FAQ block** | "Drop transcripts. Skip the questionnaire" handles setup friction. "Variety beats volume. 5 varied transcripts > 25 of one type" handles quality concerns. "What makes it different" handles differentiation. "Why it sounds like you" handles voice-skepticism. Each objection answered in the section where the buyer would raise it, not gathered into a separate FAQ. |
| 4 | **Soft paid-tier mention, single line** | Exact wording: *"Or if you'd rather we run the whole system for you, see the Playbook."* One line, placed after the primary CTA section, not a dedicated section. Self-selecting buyers click; everyone else ignores it without friction. |
| 5 | **CTA clustering: 11 CTAs, 4 unique destinations** | `/intake` (wizard) ×3 / `/playbook` (paid tier) ×2 / `#proof` anchor ×2 / GitHub ×2 / company links ×2. Same destinations repeated at multiple scroll depths so the reader can convert at the moment they're ready, not only at top or bottom. |
| 6 | **Two-audience design** | Main copy is for the SME buyer. Sections 18-20 ("For developers and ICM judges" + "Under the hood: a folder." + folder-structure code block) speak to the technical / open-source / judging audience. Smart move for an open-source + paid hybrid — the dev crowd gets their section without it dominating the buyer flow. |
| 7 | **Numbered onboarding (01 / 02 / 03)** | Sections 13-16 use explicit "01 Build your identity / 02 Drop in an artifact / 03 Get posts in your voice" framing. Reader knows where they are in the path. |
| 8 | **No illustrations or decorative graphics** | Pure typography + structured text + the LinkedIn embeds + one code block. No mockups, no diagrams, no stock photography. The product is a folder; the page mirrors that minimalism. |

### The paid-tier landing (`voiceprint.8signal.com/playbook`)

**Section sequence:**
1. Nav header
2. Hero: headline + sub-headline + 2 CTAs
3. "Who this is for" — 3 named buyer personas
4. "What's in the system" — 8 modules expanded
5. "How it works" — 3 phases (Build / Launch / Compound)
6. "The voice tunes itself" — automation/refinement narrative
7. "Investment" — two pricing tiers side-by-side (no dollar amounts)
8. Final CTA + footer

**Verbatim copy:**
- Headline: *"Your LinkedIn growth engine, run by operators."*
- Sub-headline: *"The Playbook is a complete LinkedIn system, built around your voice and executed alongside your team. Eight modules. Four-week build. Monthly execution."*

**The 8 modules (verbatim, for module-structure pattern reference):**

| # | Module name | One-line description (verbatim) |
| - | --- | --- |
| 01 | The Voice System | *"Your voice on LinkedIn, protected from AI drift."* |
| 02 | The Profile System | *"Your LinkedIn profile audited and rebuilt as a conversion tool."* |
| 03 | The Audience Map | *"Your ideal client defined in plain language."* |
| 04 | The Compliance Layer | *"Industry-specific language guardrails."* |
| 05 | The Content Engine | *"The system that turns your meetings, planning documents, weekly reviews, and client wins into LinkedIn posts in your voice."* |
| 06 | The 30-Day Cadence | *"A themed monthly rhythm built on your core values and unique positioning."* |
| 07 | The Campaign Pack | *"Multi-week themed pushes with a story arc, not random posts."* |
| 08 | The Engagement Strategy | *"The 30-minute daily routine that actually moves pipeline."* |

**Patterns observed (paid-tier landing):**

| # | Pattern | Detail |
| - | --- | --- |
| 1 | **Filter-before-features** | "Who this is for" comes BEFORE the 8-module breakdown. Three named buyer personas (fractional executives / founder-led $5M-$50M / niche operators). Cold-disqualifies wrong fits early so the buyer self-selects in or out before reading anything else. |
| 2 | **No prices on the page** | Verbatim: *"Engagement size depends on your industry, audience, and goals. We quote after the discovery call. No surprises, no upsells."* High-touch consultative sales model. |
| 3 | **Two pricing structures named, not priced** | "The Build" (one flat fee, no retainer) vs "Build + Run" (monthly retainer). Structures are visible so the buyer knows the shape of the engagement; numbers are revealed in the discovery call. |
| 4 | **No duplicate proof on the paid page** | No testimonials, case studies, or before/after metrics on the Playbook page itself. Credibility anchor is "Built and operated by 8 SIGNAL" (footer). The free tier's proof block does this work; the paid tier doesn't try to re-prove. |
| 5 | **Calendar-booking, not direct payment** | Primary CTA: *"Book a discovery call →"* (appears 4 times, links to `cal.com/8signal/discovery`). No form, no checkout, no add-to-cart. Sales is human, scheduled. |
| 6 | **Transparency-as-risk-reversal** | *"90-day post-launch voice support"* + *"No surprises, no upsells."* No money-back guarantee, no free trial. Trust is built through stated transparency, not refund offers. |
| 7 | **8 modules with single-line descriptions** | Each module is a noun-phrase title + one sentence on what it does. Reader can scan the 8 in under a minute and understand the shape of the engagement. The detail lives in the discovery call. |

### What this section is and isn't

These are the **structural patterns** observed on Voiceprint's two pages. They describe WHAT Voiceprint did. They do not prescribe what this project's sales page should say, which sections it should have, in what order, or with what copy — those decisions belong to this project's build workers (dispatched from operator/orchestrator) who know the realtor buyer, the Option C paid-tier offer, and the existing 18.5KB README copy that the new sales surface will distill from.

If you need additional research-class input — e.g., "find 3-5 comparable open-core free+SaaS landing pages so we can triangulate the pattern," or "what's the closest paid-tier landing precedent for a $10-30/mo recurring SaaS targeting solo professionals?" — that's a fresh research-claude brief, not work the realtor project needs to do itself.

---

## What this doc is NOT

This doc carries findings. It does not contain: sequencing, "Step 1 / Step 2 / Step 3," worker cost estimates, preconditions, build playbooks, sales-page CTA design, SaaS architecture, billing/multi-tenancy patterns, or any prescriptive answer to "what should this project do next." Those are this project's decisions, dispatched from operator/orchestrator/build workers — not from research-claude. If those questions need research-class input ("what are the closest precedents for open-core free+SaaS hybrids?", "how do similar products structure their conversion funnel?"), they can be sent back to research-claude as a new brief.

---

**End of handoff.**
