# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Users

Brandon and his family/partner, planning beach vacations from the Dallas/Fort Worth area. The site password is shared within the household only. Users arrive with a planning question ("where should we go, what does it cost, how long to get there") and compare options together.

## Product Purpose

A private, living travel-research hub. Its first and current surface is **The Lawson Beach Index**: a comparison of 60 all-inclusive resorts (Mexico, Central America, Caribbean, Bahamas) on verified guest ratings, real price ranges, amenities, and door-to-door travel effort from DFW. Success means the household picks trips confidently from it without re-doing research — and the hub keeps growing (more destinations and, potentially, other trip types) rather than ending with one booking.

## Positioning

A personal index the big travel sites can't be: every rating traceable to a real review page with its source linked, every flight time anchored to the family's actual home airport, zero listicle/SEO content, and completely private. It answers "for us, from DFW" — not "for everyone."

## Operating Context

- Consumed as a published website (GitHub Pages via the `Laws0x01/travel` repo) unlocked with a single shared password — no usernames.
- Updated locally: region data lives in `build/data/*.json`, `python3 build/merge.py` rebuilds the report and CSV export, `node build/encrypt.js '<password>'` produces the public `index.html`, then commit + push.
- Research refreshes are done with Claude (web research with source capture), typically per region.
- A Claude artifact and a `resorts.csv` export mirror the report for sharing/spreadsheet use.

## Capabilities and Constraints

- Static hosting only — no server, no accounts. Client-side AES-256-GCM encryption **is** the privacy mechanism; the password is not recoverable, only replaceable (re-encrypt).
- Plaintext report and data are never committed; `build/` is gitignored. The public repo carries only the encrypted `index.html` and docs.
- Current data is a snapshot (August 2026). Prices are advertised ranges for 2 adults, not quotes; ratings carry platform + review count + source URL.
- Flight data covers nonstop vs. 1-stop from DFW with scheduled durations; airports beyond the ceiling exist in the data but are flagged.
- Explicitly undecided: which destination or trip type the hub expands to next.

## Brand Commitments

- Name: **The Lawson Beach Index** (family name; user-chosen and binding).
- Access ritual: one password, no username, unlock in the browser.

## Evidence on Hand

- `build/data/*.json` — 60 resorts with per-resort review URLs (TripAdvisor / Expedia / Booking.com, captured Aug 2026), price ranges, amenities, airport distances.
- `build/data/flights.json` — verified DFW route data (nonstop durations, 1-stop ranges, frequency notes).
- `build/resorts.csv` — spreadsheet export of the full table.
- No owned photography or resort imagery. Future work must not fabricate resort photos, testimonials, or "our trip" content that didn't happen.

## Product Principles

1. **Every number is traceable or absent.** Ratings, prices, and flight times come from named real sources — never invented, never from listicles. "Not found" beats a guess.
2. **DFW anchors all travel math.** Distance is measured in the family's real door-to-door effort, not abstract geography.
3. **~5 hours of flying is the comfort line.** Content beyond it is out of scope or explicitly flagged as a longer haul.
4. **Private by default.** Nothing readable ships outside the password gate; the public repo stays opaque.
5. **Built to grow.** New destinations or indexes join the same data → build → encrypt pipeline instead of becoming one-off pages.
