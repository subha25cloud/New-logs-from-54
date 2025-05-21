
# PLUS GPT LOG 54N: DOW + SMART RANGE EXPANSION ENGINE

## Purpose:
To capture explosive moves that emerge from tight range consolidations using Dow Theory + Smart Range Breakout logic. This engine is designed for intraday and short-term swing trades that aim to enter during early phase of breakout or breakdown expansions.

## 1. Strategy Core Concept
- Dow Theory confirms whether consolidation is in context of a larger trend (HL/HH or LH/LL)
- Smart Range logic defines narrow compression zones (NR4/NR7, inside bars, volatility contraction)
- The engine identifies breakout readiness using volume build-up + structural compression and executes with early entry precision.

## 2. Instruments & Conditions
- **Best for:** Nifty50, BankNifty, ICICI, Axis, SBI, HUL, HDFC twins, Infosys
- **Timeframes:**
  - **Intraday:** 5m, 15m
  - **Swing:** 1H, 4H
- **Market Phase:** After 2+ inside bars, or narrowest candle range (NR7 type) and volume squeeze zones

## 3. Entry & Exit Logic

### Breakout (Long):
1. Price in tight range with declining ATR over 3–5 candles
2. Dow shows HL → HH formation before range
3. Volume increases slightly inside last range bar
4. Entry on breakout of high of range bar
5. **SL:** Below range low or 0.5x ATR buffer
6. **TP1:** Width of range projected from breakout point
7. **TP2:** 1.618 extension of breakout leg

### Breakdown (Short):
1. Price compresses with LH → LL structure
2. Volume contracts then spikes on breakdown
3. Entry on breakdown below range low
4. **SL:** Above range high
5. **TP1:** Range width projected below
6. **TP2:** Next fib zone or demand zone

### Exit Enhancements by Trade Type
- **PulseBot:** 3–5 candle momentum check, exit if move stalls
- **SwingBot:** Trail stop after TP1, or if structure breaks
- **OptionBot:** 30–35% stop in premium, TP = 1.5x premium or trail by price delta

## 4. ML Assignments
| ML | Role |
|----|------|
| ML1 | Detects range and breakout geometry |
| ML2 | Measures volume shift and spoofing presence |
| ML5 | Confirms structural alignment + compression probability |
| ML6 | Filters fake breakouts using trap detection |
| ML7 | Position sizing based on range width & volatility |

## 5. CNS Functions
- Approves breakout only if structure + volume + ML5 alignment > threshold
- Cancels breakout trades during macro announcements or overlapping signals
- Can combine this strategy with VWAP/OBV confirmation before activation
- Logs reason: “Smart Range breakout aligned with Dow phase”

## 6. Bot Behavior

### PulseBot:
- Primary executor for 5m/15m setups
- SL adjusts dynamically with trailing fib levels
- Avoids first 5 min breakout traps unless volume validates

### SwingBot:
- Prefers clean inside bars on 1H/4H
- Entry next candle after breakout if confirmation holds
- Uses fib projection + swing map to track momentum

### OptionBot:
- Uses breakout in direction of trend only
- Selects ATM CE/PE, exits on IV collapse or move loss >35%

## 7. UI Controls
- Toggle in dashboard: “Smart Range Engine”
- Shows compression rating (0–100)
- Displays Dow structure + last 5 candle ranges
- Visual tag for ML5 confidence (e.g. green > 75%)

## 8. Special Notes
- Works best on Monday & Wednesday (early week breakouts)
- Avoids post-news breakout (if pre-event consolidation false)
- Best used in trending assets (avoid choppy stocks)

**Next:** Log 54O – Dow + Sector Flow Alignment Strategy
