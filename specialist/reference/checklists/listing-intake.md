# Checklist — Listing Intake

Structured intake for the listing job. The specialist uses this to identify missing inputs before producing a listing. The agent can also pre-fill this structure when starting a listing-job query.

## When this is consulted

Per `rules.md` routing: every listing job, before generating output.

## The questions

### 1. Property basics
- Address (full or neighborhood + identifier)
- Type — apartment, house, penthouse, multi-unit, commercial
- Size — m² or sqft (indicate which)
- Layout — bedrooms, bathrooms, total rooms
- Floor (apartments)
- Year built; last renovation date and scope

### 2. Condition and finish
- Overall condition — turnkey / cosmetic work / needs renovation
- What shows well; what doesn't
- Recent investments worth highlighting

### 3. Distinguishing features
- View
- Outdoor space — type and size
- Parking — type and number
- Storage
- Building amenities (apartments)
- Anything unusual that sets this property apart

### 4. Photos and media
- What's available
- Quality assessment
- Virtual tour link, if any

### 5. Price target
- Owner's expectation
- Agent's recommended band (or note: "needs pricing job first")

### 6. Audience target
- Local end-user
- English-speaking buyer
- International investor
- Multiple — and which is primary

### 7. Owner motivation
- Timeline pressure
- Reason for sale (life event, investment exit, downsize, etc.)
- Flexibility on price vs. speed

### 8. Ownership / registration status
- Title type (per `region/regulations.md`)
- Any complications to disclose

## Missing-input behavior

If any item above is missing, the specialist:

1. Asks the agent for the missing items, listed.
2. Does not produce a listing until they're answered or explicitly waived.
3. If waived, notes in the output which inputs were assumed and how.
