---
date: 2026-01-11
updated: 2026-10-05
source: Hermes Agent setup
tags: [trading, signals, technical-analysis, sector-heatmap, automation, cron, reasoning-engine]
---

# Trading Signal Notifier v1.1 — Advanced Setup

## Stack
- **Python**: 3.12 venv at `/home/hermes/.venv/trading`
- **Data**: Binance OHLCV (free, no API key) via `ccxt`
- **Indicators**: pandas-ta (RSI, MACD, BB, Stochastic RSI, MA, ADX, ATR)
- **Sector Classification**: 40+ pairs mapped to 20+ sectors
- **Notifications**: Telegram `@hermes_metal_bot`
- **Python**: `/home/hermes/.venv/trading`

## File Structure
```
/home/hermes/projects/trading-bot/
├── analysis/
│   ├── mtf_engine.py          # Basic multi-timeframe engine
│   ├── reasoning_engine.py    # Advanced reasoning + TP/SL engine
│   └── auto_discover.py       # Sector heatmap + pair discovery
├── config/
│   ├── indicators.py          # Indicator configs per TF
│   └── pairs.py               # Watchlist + sector map
├── daily_report.py            # Full report (sector heatmap + reasoning + TP)
├── scan_and_notify.py         # Quick scan (15 min cron)
└── webhooks/
    └── server.py              # Flask webhook server
```

## Activation
```bash
source /home/hermes/.venv/trading/bin/activate
```

## Run Daily Report
```bash
cd /home/hermes/projects/trading-bot
python3 daily_report.py
```

## Report Features
1. **Sector Heatmap** — Scans 20+ sectors, ranks by 4H performance + RSI + volume
2. **Top Movers** — 24H gainers with sector tags
3. **High Confidence Signals** — >70% confidence signals first
4. **All BUY/SELL Signals** — With TP/SL/Risk-Reward
5. **Emerging Setups** — Auto-discovered pairs with good entries
6. **Deep Dive** — BTC & ETH reasoning breakdown
7. **Take Profit Levels** — TP1, TP2, TP3 based on ATR + S/R
8. **Stop Loss** — Calculated from ATR

## Scheduled Reports (WIB)
| Time | Job ID | Description |
|------|--------|-------------|
| 7 AM | `40b1cb334184` | Morning scan |
| 11 AM | `51e5abe66224` | Midday check |
| 3 PM | `fcbdb9b4d195` | Afternoon review |
| 10 PM | `ff9ad62231b3` | Night report |
| 1 AM | `03b0854ef60d` | Late night scan |
| 15 min | `67f25ac7a659` | Quick entry scan |

## Sector Classification
Sectors tracked: Layer 1, Layer 2, DeFi (DEX, Lending, Stablecoin, Perpetuals, Liquid Staking), AI (Compute, GPU, Agents, ML), DePIN, Gaming, Meme, Exchange, Institutional, Oracle, Storage, BTC L2, Interoperability, Data Availability

## Signal Scoring
- Score >= 4 + HTF alignment = actionable signal
- Confidence = score/10 * 100 (max 95%)
- BUY: HTF bullish + oversold + bullish patterns
- SELL: HTF bearish + overbought + bearish patterns

## Telegram
- Bot: `@hermes_metal_bot`
- Token: `/tmp/hermes_telegram_token`
- Chat ID: `7768094471` (Totale Metal)

## Todo
- [ ] Add more pairs to sector map
- [ ] Win rate tracking (log signals + outcomes)
- [ ] TradingView webhook endpoint
- [ ] Backtesting module
- [ ] More sophisticated reasoning (market structure, order flow hints)
