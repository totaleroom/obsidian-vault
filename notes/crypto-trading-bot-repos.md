# High-Starred Crypto Trading Bot GitHub Repos — Research Summary

## Methodology
- Searched GitHub API for Python-centric crypto trading bot repos
- Filtered for: backtesting, strategy optimization, risk-reward ratio, multi-timeframe, technical indicators
- Prioritized stars >1,000 where available

---

## Top 5 Repositories

### 1. freqtrade/freqtrade — 55,026 stars ⭐
**URL:** https://github.com/freqtrade/freqtrade  
**Language:** Python (5.4M LOC)  
**Topics:** algorithmic-trading, trading-bot, cryptocurrencies, freqtrade, bitcoin

#### What Makes It Notable
- Largest open-source crypto trading bot by an enormous margin
- Full backtesting engine with **walk-forward validation (CPCV)**
- **HyperOpt**: ML-based strategy optimization via hyperoptable parameters and custom loss functions
- FreqUI dashboard + Telegram bot control
- Supports **100+ exchanges** via CCXT
- Custom stoploss modes: absolute, open-trade, trailing, dynamic
- Minimal ROI configuration per time bucket
- Multi-currency pairlist management (VolumePairList, etc.)
- Dry-run and live trading modes

#### Strategy Concepts Implemented
- **Multi-timeframe analysis** via `@informative` decorator (e.g., 5m strategy signals informed by 1h BTC data)
- `populate_entry_trend()` / `populate_exit_trend()` for entry/exit signal generation
- Protections: CooldownPeriod, Unclogger, MaxRuntime
- Stoploss: trailing (configurable step), absolute, dynamic
- Custom hyperoptable ROI/stoploss parameters
- Signal tagging (`enter_tag`, `exit_tag`) for trade attribution

#### Optimization Techniques
- **HyperOpt** with custom loss functions: Sharpe, Sortino, Calmar, MaxDrawdown, profit-only
- **Walk-forward analysis** using CPCV (Contingent Pair Per Day Constraint)
- Hyperoptable parameter space for: indicators, ROI tables, stoploss, exit signal weights, entry/exit params
- Pre-downloaded historical data from exchanges for reproducible backtests
- Lookahead analysis tools to detect future-leakage in strategies

---

### 2. iterativv/NostalgiaForInfinity — 3,447 stars ⭐
**URL:** https://github.com/iterativv/NostalgiaForInfinity  
**Language:** Python (18.7M LOC)

#### What Makes It Notable
- Most sophisticated public Freqtrade strategy with 8 variants (X, X2–X8)
- Designed for **5-minute timeframe** with 6–12 open trades and unlimited stake
- **Volume pairlist** with 40–80 pairs
- Detailed backtest results published per GitHub commit
- Comprehensive docs: iterativv.github.io/NostalgiaForInfinity

#### Strategy Concepts Implemented
- Custom momentum/mean-reversion signal confluence
- `use_exit_signal` + `ignore_roi_if_entry_signal` combination for signal-aware exits
- ROI tables tailored per variant
- Blacklist management for leveraged tokens (`*BULL`, `*BEAR`, `*UP`, `*DOWN`)
- Entry/exit signal customization via Freqtrade hooks
- Signals informed by custom indicators from `freqtrade/technical`

#### Optimization Techniques
- Per-commit backtest result tracking
- Variant-specific parameter tuning (X1–X8 each have different ROI/stoploss profiles)
- Custom pairlist configuration per variant

---

### 3. Rikj000/MoniGoMani — 1,026 stars ⭐
**URL:** https://github.com/Rikj000/MoniGoMani  
**Language:** Python (306K LOC)  
**Topics:** hyperopt, weighted-signals, machine-learning, freqtrade-framework

#### What Makes It Notable
- Explicitly a **HyperOpt framework**, not just a single strategy
- **Weighted signal approach**: 25+ signals can each have their weights hyperopted
- Partially automated optimization workflow documented step-by-step
- Companion hyperopt loss functions included
- Full documentation: monigomani.readthedocs.io

#### Strategy Concepts Implemented
- **Weighted signal framework**: multiple signals combined via weight sum; weights are HyperOpt parameters
- Assigns weights to different entry/exit conditions (momentum, mean-reversion, breakout signals)
- Multi-signal confluence: signals with weight above threshold trigger entry/exit
- Customizable minimal ROI + stoploss per variant
- Framework for building your own weighted strategy with logical constraint layers

#### Optimization Techniques
- **HyperOpt of signal weights** — the core differentiator; each signal has a weight parameter
- Loss function: custom MoniGoMani loss functions for hyperopt
- Logic-aware optimization: suggests running optimization with logical constraints, not blind brute-force
- Re-optimization recommended after manual changes

---

### 4. xFFFFF/Gekko-Strategies — 1,442 stars ⭐
**URL:** https://github.com/xFFFFF/Gekko-Strategies  
**Language:** JavaScript (4.5M LOC)  
**Topics:** gekko, strategies, backtest-database, technical-analysis, trading-algorithms

#### What Makes It Notable
- **Largest backtest database**: 100+ strategies with results in `backtest_database.csv`
- Screenshots of backtest performance per strategy
- Historical data-backed results (not theoretical)
- Strategies ranked by best profit/day on unique datasets
- Multi-exchange support (Binance, Bitfinex, etc.)

#### Strategy Concepts Implemented
- **RSI strategies**: RSI, RSIc狗, and RSI variants
- **EMA/MACD crossover** strategies
- **Bollinger Bands** strategies
- Multiple timeframes: 1m, 5m, 15m, 1h, etc.
- Grid trading strategies
- Trend following and mean-reversion variants
- Dark cloud, engulfing candlestick patterns

#### Optimization Techniques
- Backtest results stored in CSV for comparison
- BacktestTool for batch parameter optimization
- Unique dataset benchmarking for strategy comparison

---

### 5. freqtrade/technical — 1,034 stars ⭐
**URL:** https://github.com/freqtrade/technical  
**Language:** Python (119K LOC)  
**Topics:** technical-analysis, freqtrade, dataframe

#### What Makes It Notable
- **Official indicator library** for the Freqtrade ecosystem
- **50+ custom indicators** collected/developed, ready to use in `populate_indicators()`
- Advanced TA: Ichimoku Cloud, Laguerre RSI, Schaff Trend Cycle
- PyPI package: `pip install technical`
- Comprehensive docs with examples

#### Strategy Concepts Implemented (Indicator Catalog)
- **Consensus models** (TradingView-style): MovingAverage Consensus, Oscillator Consensus, Summary Consensus
- **Volume indicators**: VFI (Volume Flow Indicator), VPCI (Volume Price Confirmation), VWMA
- **Trend indicators**: MMar (Madrid Moving Average Ribbon — 4-category trend classification), ADX
- **Momentum**: Laguerre RSI (low-noise, John Ehlers), STC (Schaff Trend Cycle)
- **Range indicators**: Bollinger Bands, ATR, historical volatility
- **Chart patterns**: Ichimoku Cloud, Pivot Points, Trendlines (2 algorithms), Fibonacci retracements
- **Pattern detection**: candlestick pattern helpers

---

## Bonus Repository

### freqtrade/freqtrade-strategies — 5,523 stars ⭐
**URL:** https://github.com/freqtrade/freqtrade-strategies  
**Language:** Python (370K LOC)  
**Topics:** freqtrade-strategies, trading-strategies

- Official Freqtrade strategy repository
- `hyperopts/` folder with pre-optimized hyperparameter sets
- `strategies/` folder with ready-to-use strategy classes
- Backtest results published alongside code
- Multiple strategies: EMA, RSI, MACD, ADX-based entry/exit

---

## Cross-Cutting Findings

### Risk-Reward Ratio Optimization
- **Freqtrade**: `minimal_roi` dict (time-based ROI targets), hyperoptable `stoploss` (absolute or trailing)
- **MoniGoMani**: custom loss functions for hyperopt targeting risk-adjusted returns
- **NostalgiaForInfinity**: per-variant ROI tables; stoploss profiles tuned per variant

### Trading Strategies Found
| Strategy Type | Repos |
|---|---|
| Momentum | MoniGoMani (weighted signals), freqtrade-strategies |
| Mean Reversion | NostalgiaForInfinity, Gekko-Strategies (RSI/BB) |
| Breakout | freqtrade (custom), NostalgiaForInfinity variants |
| Multi-timeframe | Freqtrade (`@informative`), NostalgiaForInfinity |
| Consensus (multi-indicator) | freqtrade/technical (consensus models) |

### Multi-Timeframe Analysis
- **Freqtrade**: `@informative` decorator for cross-timeframe data (e.g., 1h signals on 5m strategy)
- **NostalgiaForInfinity**: uses 5m with volume pairlist + custom timeframe configs
- **Freqtrade/technical**: indicators support multi-timeframe resampling

### Technical Indicators Used
- Trend: EMA, SMA, VWMA, MMar, Ichimoku Cloud, ADX
- Momentum: RSI, Laguerre RSI, STC, MACD, VFI, VPCI
- Volatility: Bollinger Bands, ATR, Fibonacci retracements, trendlines
- Volume: OBV, VFI, VPCI, VWMA
- Custom: Consensus models, SMC (Smart Money Concepts) patterns

### Optimization Techniques
1. **HyperOpt** (Freqtrade): Bayesian optimization over parameter space
2. **Walk-forward validation** (CPCV): sliding window out-of-sample testing
3. **Custom loss functions**: Sharpe ratio, Sortino ratio, Calmar ratio, MaxDrawdown
4. **Weighted signal framework**: MoniGoMani's core approach
5. **Batch backtesting**: Gekko BacktestTool for parameter sweeps
6. **Lookahead analysis**: Freqtrade tools to detect future-leakage

---

## Gap: High-Star (>1k) Python-Only Algo Trading Repos
Most very-high-star Python algotrading repos focus on **generic finance** (e.g., zipline, backtrader) rather than crypto-specific bots. The crypto-specific ecosystem is dominated by:
- **Freqtrade** (55k stars) — by far the leader
- **Gekko** (strategy repo at 1.4k stars, but Gekko itself is older Node.js)
- **Jesse** (much smaller community, ~low hundreds of stars)
- **Hummingbot** (CoinAlpha, institutional-grade but more market-making focused)

For crypto-native strategy implementations with multi-timeframe analysis, risk-reward optimization, and backtesting, **Freqtrade and its ecosystem** are the clear standard-bearers.
