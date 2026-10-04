---
date: 2026-01-11
source: Hermes Agent research
tags: [affiliate, scraping, shopee, tokopedia, browser-automation, pipeline]
---

# Affiliate Scraping Pipeline — Celana Denim Pria Barrel

## Context
Build AI agent pipeline for affiliate marketing:
1. Product research (scraping marketplaces)
2. Content generation (storytelling)
3. Social posting (Threads/Meta)

## Products Scraped (2026-01-11)

Source: Google Shopping (bypasses marketplace anti-bot)
Search: "celana denim pria loose barrel regular site:shopee.co.id OR site:tokopedia.com"

| Product | Price | Sold | Source |
|---------|-------|-------|--------|
| CELANASTUDIO Celana Jeans Denim Pria Lebar | Rp 274.900 | 2rb+ terjual | Tokopedia |
| HASIER Barrel Core Jeans Vintage Blue | Rp 404.100 | - | Tokopedia |
| Rockmaker Celana Denim Regular Loose Fit | Rp 184.900 | - | Shopee |
| Meaning Circle Barrel Jeans - Jebarrel Blue | Rp 257.900 | - | Tokopedia |
| CELANA BARREL JEANS PRIA VINTAGE OVERSIZE | Rp 150.000 | - | Tokopedia |
| Ripped Jeans Regular Fit Pria | Rp 196.020 | - | Tokopedia |
| UNISEX Baggy Barrel Jeans Raw Denim | Rp 35.000 | - | Shopee |

## Tech Stack Installed (VPS)

| Component | Status | Path |
|-----------|--------|------|
| browser-use 0.13.10 | ✅ Working | `/home/hermes/.venv/browser-automation` |
| invisible-playwright 0.70.10 | ✅ Working (xvfb) | same venv |
| playwright 1.63.0 | ✅ Chromium installed | same venv |
| GLM-5.3-Flash | ✅ sumopod endpoint | `ai.sumopod.com/v1` |
| xvfb | ✅ Installed | `/usr/bin/Xvfb` |

### Activate venv
```bash
source /home/hermes/.venv/browser-automation/bin/activate
```

## Blocker: Anti-Bot

### What Blocked
- **Shopee.co.id** — login wall / error page (no products rendered)
- **Tokopedia.com** — "produk nggak ditemukan" / CAPTCHA
- **Lazada.co.id** — empty catalog
- **Google redirect URLs** — `/url?` links blocked, `decode_google_url()` returns empty
- **browser-use agent on Google** — CAPTCHA page detected

### What Works
- **Google Shopping search results** — text extraction works
- **invisible-playwright + xvfb** — stealth Firefox bypasses some blocks

### Solutions to Implement

1. **Undetectable** (undetected-chromedriver fork)
   - Patches Selenium/Playwright to appear as real Chrome
   - npm: `undetected-chromedriver`
   
2. **Selenium stealth** — `selenium-stealth` (npm)
   - Blocks detection: `navigator.webdriver`, `automationDetector`
   
3. **Residential proxies** — critical for high-volume scraping
   - Services: BrightData, Oxylabs, SmartProxy
   - Indonesian IPs available
   
4. **Rotate User-Agents + fingerprints**
   - playwright-extra + stealth-plugins
   
5. **Shopee/Tokopedia API** (official)
   - Shopee Affiliate API: https://affiliate.shopee.co.id
   - Tokopedia Creator: https://creator.tokopedia.com
   
6. **Scraping APIs** (third-party)
   - SerpAPI (Google Shopping)
   - ScraperAPI
   - BrightData Web Unlocker

## Pipeline Draft

```
Step 1: browser-use agent
  → Google Shopping search (invisible-playwright)
  → Extract product names, prices, sources
  
Step 2: Hermes (this session)
  → Generate casual Indonesia storytelling content
  → Attach affiliate links from Shopee/Tokopedi affiliate dashboard
  
Step 3: Post
  → Zernio API (blocked — billing issue)
  → OR Meta Graph API direct (needs setup)
```

## Content Generated (Draft — Casual Indonesia)

```
🚴‍♂️ Celana Denim Barrel — yang ini LOH BRO

Gw ulang-ulang scroll Shopee Tokopedia 
tapi yang ini MAU GAK MAU gw harus bilang:
"terlalu murmer buat流出成这样"

Nih 3 yang sekarang lagi rame:

1️⃣ HASIER Barrel Core Jeans — Rp 404.100
   Vintage Blue, barrel cut — lebar di paha, rapet di bawah
   Regular fit proporsional

2️⃣ CELANASTUDIO — Rp 274.900 (2rb+ terjual)
   Striped Wide Loose Trousers

3️⃣ Rockmaker Regular Loose Fit — Rp 184.900
   Mineral Blue, daily cocok

—
Kenapa barrel/loose cut lagi trending?
Karena celana skinny udah capek.

#celanadenim #barreljeans #loosefit #denimpria #streetwearindonesia
```

⚠️ Need to split into thread chain (500 char limit)

## Next Steps

- [ ] Generate Shopee/Tokopedia affiliate links for scraped products
- [ ] Setup Meta Graph API for direct Threads posting
- [ ] Resolve Zernio billing (payment required)
- [ ] Implement stealth browser for direct marketplace scraping
- [ ] Create content variation templates
- [ ] Setup cron job for daily product research

## Related Notes

- [[Shopee-Affiliate-Setup]]
- [[Threads-Posting-Pipeline]]
- [[AntiBot-Research]]
