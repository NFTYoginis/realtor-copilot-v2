# Cold-Test Brief — for the Two Validation Agents

A short, practical brief for the two practicing agents running real-environment validation on Realtor Copilot v2: the Jerusalem agent (working full-time in Jerusalem) and the Marin agent (working full-time in Novato / Marin County). Each receives the deliverable, runs it against real properties they're working *this week*, and reports what worked and what didn't.

This is the v2.1 priority. Findings feed the universal files (never the region files).

---

## What we need from you

Three to five real interactions with the specialist, captured as transcripts (copy/paste from your Claude Project chat). For each interaction, a 2–3 line note answering:

1. **Did the output land?** (Could you actually use it, hand it to a client, or copy/paste it into your CRM?)
2. **What was wrong, missing, or confusing?**
3. **What surprised you — good or bad?**

That's it. Don't write a report. The transcripts + your one-paragraph reactions are enough.

---

## Setup (about 20 minutes, one time)

1. Go to [github.com/NFTYoginis/your-market-realtor](https://github.com/NFTYoginis/your-market-realtor)
2. Click the green "Code" button → "Download ZIP". Unzip it.
3. **Copy the populated case-study region into your specialist folder:**
   - **Jerusalem agent:** copy the contents of `case-studies/jerusalem/region/` into `specialist/reference/region/` (overwrite the placeholder files).
   - **Marin agent:** copy the contents of `case-studies/novato/region/` into `specialist/reference/region/` (overwrite the placeholder files).
4. **Skim `specialist/reference/region/services.md`** — it ships with illustrative example vendor entries. Either replace 2–3 categories with your *actual* vendors, or leave it as-is (the test still works; we just won't be able to validate the services-lookup job against your real Rolodex).
5. Go to [claude.ai](https://claude.ai) → Projects → New Project → name it "Realtor Copilot Test".
6. In the project, click "Add to project knowledge" → upload the entire `specialist/` folder (drag-and-drop is fine).
7. Start a new chat in that Project.

The copilot should greet you with a five-job menu. If it does not, tell us — that's a v2 bug.

---

## What to test (suggested — feel free to deviate)

### Test 1 — Listing description (your most recent listing)

Pick a listing you wrote copy for *this week*. Tell the copilot:

```
Listing job. [Property specs]. Audience: [buyer pool — e.g., "international investor",
"local end-user", "English-speaking couple relocating from out of state"].
[Bilingual flag if your market needs it.]
```

Compare the copilot's output to what you actually published. **Honest question: which would you actually use?** If neither, why?

### Test 2 — Buyer–property matching (a real buyer this week)

Pick one of your active buyers. Paste their profile (1–2 lines), then 2–4 listings you're considering showing them. Ask:

```
Matching job. Buyer: [profile]. Listings: [list]. Rank fit.
```

Read the output. **Specific check:** does the friction section call out things that are actually true about your buyer? Does the reasoning chain on the top pick read like something you could hand to the buyer? Does it call out anything you missed?

### Test 3 — Pricing band (a recent or upcoming listing)

Pick a property you've priced (or are about to price). Tell the copilot:

```
Pricing job. Property: [specs]. Owner timeline: [...]. What should I list at?
I want a band with reasoning.
```

Compare the band to what you priced at (or what you're planning). **Honest question:** is the reasoning defensible enough that you'd hand it to a seller in a listing presentation?

### Test 4 — Showing notes (NEW IN v2)

Pick a showing you did recently. Either:

**(a) Dictate fresh:** open your phone's voice memo, talk for 60–90 seconds about what happened at the showing — buyer reactions, friction, comparisons made, your read. Transcribe it (Apple Voice Memos transcribes automatically, or use any tool). Paste into the chat.

**(b) Type it from memory:** 5–10 lines of "what happened" is plenty.

Frame it:

```
Showing notes job. Showing was [date] at [property]. Buyer: [identifier].
Here's my dictation: [paste]
```

Read the structured note. **Specific check:** does the friction section capture what the buyer actually flagged? Are the tags useful? Would you use this note again next week if you were running a matching job for the same buyer?

### Test 5 — Services lookup (NEW IN v2)

Ask the copilot:

```
Who's in my services list for [a category — inspectors, lenders, stagers, whatever]?
```

If you populated the file with your real vendors, the copilot should surface your top pick with reasoning. If you left the illustrative entries in, the copilot will surface those — note that the *behavior* is what matters (does it cite from the file, never invent? does it flag stale entries?).

---

## Reporting back

The simplest path: **email or message the author the chat transcripts plus a 1–3 paragraph reaction.** No template. Free-form.

If you'd prefer a structured form, this works:

```
Test 1 — Listing
[Copy/paste of your prompt]
[Copy/paste of the copilot's reply]
Did it land? [Y/N + one sentence why]

Test 2 — Matching
[Same]

...

Overall reaction:
[A paragraph or two. What surprised you? What was wrong? What did you wish it did?]
```

---

## What we're specifically watching for

These are the things v2's design assumes will work. Tell us if any *don't*.

- **The buyer-fit reasoning chain on the top pick reads like a real recommendation, not a checklist.**
- **The pricing band has comp logic an agent could defend.**
- **The showing-note friction tags are normalized and useful** (e.g., consistent across notes for the same buyer).
- **Services lookup never invents a vendor** — even when asked broadly.
- **The welcome menu doesn't get in the way.** If you opened a chat with a clear job request, did the copilot skip the menu and go to the job? Or did it stop you with the menu first? (The latter is a bug.)
- **Voice rule:** does the copilot ever address your client directly, or does it always speak to you? (Direct-to-client output is a bug.)

---

## What NOT to test

These are out of scope for v2 and shouldn't be expected to work:

- Asking it to write a marketing flyer or IG post.
- Asking it to draft a follow-up email to a seller or buyer.
- Asking it to predict the market in 2027.
- Asking it about your personal investment decisions.
- Asking it to recommend a vendor not in your services list.

If you ask any of these, the correct behavior is a polite redirect, not a refusal-with-shame. Confirm the redirect lands cleanly.

---

## Timeline

No strict deadline — fit it into a week of normal client work. Three to five real interactions captured as you do them is more useful than ten manufactured ones at the end of the week.

If you hit something genuinely broken (the copilot ignores the menu, addresses your client directly, invents a vendor, refuses something it shouldn't), flag it the same day so it can be fixed before the next test.

---

## Thank you

This is the part of the project that no amount of simulated testing replaces. The architecture either survives contact with a real listing on a Tuesday or it doesn't. Your real reactions are the calibration data for v2.1.
