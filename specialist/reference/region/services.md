# Local Services — [MARKET NAME]

The agent's vetted list of service providers they refer clients to. The specialist consults this file when the agent asks a "look up a local service" question, or when a job context requires a vendor recommendation (e.g., a pricing memo flags "verify roof condition — call [roofer]").

This file is a **knowledge base, not a directory.** Only list providers the agent personally trusts and would recommend by name.

## Format per entry

```
**Name + role**
- Specialty / when to use: [...]
- Contact: [phone / email / website]
- Notes: [turnaround, pricing tier, what they're best at, gotchas]
- Last updated: [YYYY-MM-DD]
```

## Categories

### Inspectors
[PLACEHOLDER — list 1–3 with specialties, e.g., older homes, foundation, septic, mold]

### Lenders / mortgage brokers
[PLACEHOLDER — distinguish conforming vs. jumbo vs. portfolio if your market needs it]

### Title / escrow / closing attorney
[PLACEHOLDER]

### Stagers
[PLACEHOLDER — virtual stagers separate from physical if you use both]

### Photographers / videographers
[PLACEHOLDER — drone-licensed if your market values aerial]

### Contractors / handymen / general repairs
[PLACEHOLDER]

### Painters
[PLACEHOLDER]

### Movers
[PLACEHOLDER — local-only vs. interstate/international if relevant]

### Cleaners — listing prep & post-close
[PLACEHOLDER]

### Insurance agents
[PLACEHOLDER]

### Accountants / tax (real-estate-familiar)
[PLACEHOLDER]

### Property management
[PLACEHOLDER]

### Specialty (pool, septic, foundation, mold, structural, arborist, etc.)
[PLACEHOLDER — only categories your market actually uses]

## Rules for the specialist

- **Never recommend a vendor not in this file.** If a category is empty or `[PLACEHOLDER]`, say so and offer to help the agent populate it next time.
- **Surface as the agent's relationships, not your suggestions.** Phrasing: "From your services list, you've worked with [Name] for [specialty]" — never "I recommend [Name]." The agent owns these relationships; you retrieve.
- **Date check.** If `Last updated` is more than 12 months old, flag it: "this entry is from [date] — verify it's still current before passing on."
- **Match to context.** If the job is a pre-listing inspection on a 1928 building, surface inspectors with older-home specialty first. If a buyer is jumbo-financing, surface jumbo-experienced lenders.
- **One name, not three.** When the agent asks for a vendor, surface their top pick first with reasoning. Offer alternatives only if asked or if the top pick doesn't match the context.
- **Privacy.** This file is part of the agent's Claude Project knowledge base. It does not get shared with clients directly. The agent may copy specific entries into client-facing emails — never produce a "vendor list email" without the agent explicitly asking.
