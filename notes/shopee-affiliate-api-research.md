---
date: 2026-01-11
source: Hermes Agent research
tags: [affiliate, shopee, API, scraping, anti-bot]
---

# Shopee Affiliate API Research

## Status: ❌ No Public API Available

### What We Found

**Shopee Affiliate Dashboard:** `affiliate.shopee.co.id`
- Requires login — all endpoints return `{"code":30001,"msg":"no login"}`
- No public programmatic API documented
- Internal API endpoints (from JS bundle analysis):
  - `POST /api/v3/offer/batch_product_links` — link generation (needs auth)
  - `GET /api/v3/config/` — config (404 without auth)
  - `POST /api/v1/auth/login` — login endpoint (needs credentials)
  - `GET /api/v1/payment/billing_detail/invoice` — billing (needs auth)

### How Links Work (Affiliate)

Affiliate link format:
```
https://shopee.co.id/product-name-i.${shop_id}.${item_id}?sm_source=${affiliate_code}&sm_campaign=...
```

Shopee uses a link decorator system. To generate trackable affiliate links, you need:
1. Login to affiliate.shopee.co.id
2. Search product → click "generate link"
3. The system creates a decorated URL

**No way to generate links programmatically without login credentials.**

## Alternatives

### Option 1: TikTok Affiliate (has public API docs)
- URL: `https://affiliate.tiktok.com`
- Has OAuth + REST API for link generation
- Commission structure similar to Shopee

### Option 2: Tokopedia Affiliate
- URL: `https://creator.tokopedia.com`
- Official creator/affiliate program
- May have API access for registered creators

### Option 3: Manual Link Generation
- User logs into Shopee Affiliate dashboard manually
- Generates links for target products
- Stores links in a shared doc/spreadsheet
- Hermes reads from that doc to attach to content

### Option 4: Third-Party Scraping APIs
- **SerpAPI** (~$50/mo) — Google Shopping results with affiliate potential
- **BrightData Web Unlocker** (~$50/mo) — bypasses anti-bot
- **ScraperAPI** (~$50/mo) — handles anti-bot

### Option 5: Build Own Scraper
- Use residential proxies (BrightData ~$15/GB)
- undetected-chromedriver or selenium-stealth
- Risk: account ban if detected

## Recommendation

**Most practical path for now:**
1. User manually generates 5-10 affiliate links from Shopee Affiliate dashboard
2. Stores them in a Notion/Google Sheet
3. Hermes reads links via API
4. Generates content with those specific product links
5. Post to Threads

This avoids anti-bot issues entirely and gives us real trackable links.

## Related
- [[affiliate-scraping-pipeline-2026]] — full pipeline draft
- [[Threads-Posting-Pipeline]]
