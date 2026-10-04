---
date: 2026-01-11
source: Hermes Agent setup
tags: [trading, signals, technical-analysis, automation, cron]
---

# Trading Signal Notifier — Setup

## Stack
- **Data source**: Binance OHLCV (free, no API key) via `ccxt`
- **Indicators**: pandas-ta (RSI, MACD, BB, Stochastic RSI, MA confluence)
- **Multi-timeframe**: 1W, 1D, 4H, 1H, 5m
- **Notifications**: Telegram bot `@hermes_metal_bot`
- **Python**: 3.12 venv at `/home/hermes/.venv/trading`

## File Structure
```
/home/hermes/projects/trading-bot/
├── analysis/
│   └── mtf_engine.py      # Multi-timeframe analyzer
├── config/
│   └── indicators.py       # Indicator configs per TF
├── scan_and_notify.py      # CLI scanner + Telegram sender
├── send_report.py         # Full report to Telegram
└── webhooks/
    └── server.py          # Flask webhook server
```

## Activation
```bash
source /home/hermes/.venv/trading/bin/activate
```

## Run Scan
```bash
cd /home/hermes/projects/trading-bot
python3 scan_and_notify.py
```

## Cron Job
- Job ID: `67f25ac7a659`
- Schedule: `*/15 * * * *` (every 15 minutes)
- Delivers to: Telegram (@TotaleMetal)

## Telegram Token
- Bot: `@hermes_metal_bot`
- Token stored at: `/tmp/hermes_telegram_token`
- Chat ID: `7768094471` (Totale Metal)

## Indicators Per Timeframe

| Timeframe | Primary Focus |
|-----------|-------------|
| 1W, 1D | Trend (MA crossover), RSI, MACD direction |
| 4H, 1H | Momentum (RSI, MACD cross), BB squeeze |
| 5m | Entry timing (candlestick patterns, BB touch) |

## Signal Score System
- Score >= 4 = actionable signal
- BUY: HTF trend aligned + oversold/reversal signals on lower TFs
- SELL: HTF trend aligned + overbought/reversal signals on lower TFs

## Next Improvements
- [ ] Add support/resistance levels to alerts
- [ ] TradingView webhook endpoint (`/webhook/tradingview`)
- [ ] More pairs (AVAX, LINK, DOGE, ADA)
- [ ] Backtesting module
- [ ] Win rate tracking
