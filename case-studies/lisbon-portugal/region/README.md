# Lisbon, Portugal — Case Study Region Pack

Populated example region for **Lisbon (and adjacent coastal market — Cascais/Estoril when relevant)**. Use this pack as a starting template for any agent working a Portuguese urban international-buyer market, or as-is for Lisbon proper.

## Why Lisbon

Lisbon proves the architecture against a **mainstream international-buyer European market** — distinct from the v1 case studies in three ways:

| Case study | Market shape |
|---|---|
| Jerusalem | International + diaspora-driven, complex title types (Tabu / Khevra Meshakenet), bilingual Hebrew + English |
| Novato/Marin | Universal-logic-without-foreign-hook (no foreign-buyer dependency) |
| Khao Lak | Resort, foreign-buyer-dominant, leasehold/freehold structure |
| **Lisbon** | **Mainstream urban European, post-Golden-Visa international flow (Brazilians, North Americans, French), Roman-law title system, multilingual (Portuguese + English + sometimes French)** |

## What ships in this pack

Six populated files matching the v2 region structure:

- `market.md` — Lisbon market overview, adjustment magnitudes, days-on-market, foreign-buyer activity by buyer pool
- `neighborhoods.md` — central Lisbon districts + Cascais/Estoril, with anchors and buyer-pool fits
- `regulations.md` — IMT (transfer tax), IS (stamp duty), IMI/AIMI (property tax), Alojamento Local (short-term-rental) rules, post-Golden-Visa visa pathways
- `contracts.md` — CPCV (promissory contract), escritura, Caderneta Predial, Certidão de Teor, common gotchas
- `glossary.md` — local property and legal terms (Portuguese + English)
- `services.md` — illustrative vendor list with Portuguese-market specialties (multilingual lawyers, AL specialists, multilingual property managers, etc.)

## Authoring note

This pack reflects general Lisbon-market knowledge as of early 2026 and is intended as a *starting template* for a working Lisbon agent to refine with their own first-hand specifics. It is not a substitute for lived market expertise. If you work Lisbon and notice anything wrong, please open an issue or PR.

Tax rates, regulatory windows (especially Golden Visa / D7 / D8 visa programs), and Alojamento Local licensing zones change frequently — verify against the relevant authority before relying on any specific number. Currency in this pack is EUR throughout.

## How to use this pack

1. Copy the contents of `case-studies/lisbon-portugal/region/` over `specialist/reference/region/`.
2. Edit any market specifics that don't match your particular sub-market (e.g., if you specialize in Cascais coast vs. central Lisbon, weight `neighborhoods.md` toward Cascais entries).
3. Replace the illustrative vendor entries in `services.md` with your actual vendor list.
4. Drop the `specialist/` folder into a Claude Project.
