# Crochet Market Tracker

**Into the Scrape-Verse Hackathon — WeMakeDevs x Bright Data (Aug 17–23, 2026)**

A self-healing scraper that tracks crochet and handmade listings on Etsy — pricing, demand signals, and market trends — built to power real market research for [BaliCreates](#) and a future crochet-focused marketplace.

## The problem

Small handmade sellers (crochet makers, in particular) have no easy way to see what's actually selling, at what price, and what buyers care about. Existing tools are built for big e-commerce, not niche craft markets. This scraper turns Etsy's public listings into structured market signal — a foundation for pricing guidance, trend spotting, and eventually a dedicated crochet marketplace.

## What it does

The scraper pulls live crochet listings from Etsy search results and extracts structured fields per listing — title, price, shop, listing URL, and demand signals like favorites, ratings, and review tags.

Built using **Bright Data's Scraper Studio CLI** (`@brightdata/cli`), which builds extraction logic from a **plain-language description** instead of hardcoded CSS selectors. That's the self-healing part: when the page structure changes, or the schema needs to grow, you don't touch selectors — you just re-describe what you want, and it rebuilds itself around the new shape of the page.

## Self-healing in action (the demo)

| | v1 — `crochet-tracker` | v2 — `crochet-tracker-v2` |
|---|---|---|
| Fields extracted | title, price, shop, url, favorites | + **tags, rating, review_count** |
| Method | Plain-language description → AI-built collector | Same site, re-described with richer requirements |
| Result | 39 real Etsy listings scraped successfully | Same listings, now with demand + quality signals |

No selectors were rewritten by hand. The schema was extended by simply describing the new fields in natural language, and the collector rebuilt its own extraction logic — the same resilience that would kick in if Etsy changed its page layout mid-scrape.

**Collector IDs:**
- v1: `c_msxbxw1z2h7tmwq8j1`
- v2: `c_msxfxxh91267gmb4xp`

## Sample insight from the data

- "Crochet Hook Bracelet" — 2,163 favorites at a low price point, high demand-to-price ratio
- "5-in-1 Fairy Crochet Doll Pattern Bundle" — 16,430 favorites, showing strong demand for multi-pattern PDF bundles over single physical items
- Ratings cluster tightly around 4.7–5.0 across sellers, suggesting quality isn't a major differentiator — price and uniqueness likely drive purchase decisions more

## Tech stack

- **Bright Data Scraper Studio / CLI** (`npx @brightdata/cli`) — scraping + self-healing extraction
- **Etsy** — target data source (crochet search results)
- Output: structured JSON per listing, ready to feed into analysis or a dashboard

## Known limitations

- A handful of listings show malformed `price.value` fields (likely a decimal-parsing edge case from Etsy's price formatting) — flagged for a follow-up fix, not hidden.
- Currently single-keyword ("crochet") search; multi-keyword category tracking (bags, amigurumi, cardigans, etc.) is the natural next step.

## Next steps

- Schedule recurring runs to track price/trend changes over time
- Build a lightweight dashboard: top tags, average price by category, favorites-to-price ratio
- Feed insights directly into the crochet marketplace concept as seller-facing market data

---
Built by Bali (Vaibhavi Khandra) for Into the Scrape-Verse, using Bright Data Scraper Studio.
