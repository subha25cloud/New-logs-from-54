
# PLUS GPT LOG 54O: DOW + SECTOR FLOW ALIGNMENT STRATEGY (FINAL VERSION)

## Purpose:
To align trade decisions with prevailing sectoral momentum using Dow Theory for structure filtering and sector rotation logic to prioritize trades in outperforming or underperforming sectors. This strategy enhances probability by ensuring trades align with macro money flow into sectors.

---

## 1. Strategy Core Concept
- Dow Theory provides market structure (HH/HL or LH/LL) validation for any instrument.
- Sector Flow Engine maps capital rotation between sectors to detect outperformers and laggards.
- Trade is triggered only if the instrument’s structure and its sector strength agree.

---

## 2. Instruments & Usage Scope
- Stocks grouped by NSE sector index (e.g., Nifty IT, Nifty Bank, Nifty Auto)
- Intraday + Swing friendly: 15m–1H for intraday, 1H–Daily for swing
- Pairs Well With: RSI Divergence (Log 49A), OBV Trend Confirmation (Log 54G), Smart Range Breakouts (Log 54N)

---

## 3. Entry & Exit Rules

### Buy Setup:
1. Stock shows HL → HH structure (Dow Uptrend)
2. Corresponding sector index also in HH-HL structure
3. RSI > 55 and OBV showing accumulation (rising trend or breakout)
4. Stock is outperforming sector (Beta > 1 or % move > sector index in last 2 days)
5. Entry above last bullish candle or breakout zone after candle close
6. SL: Below recent swing low (or 0.7x ATR buffer)
7. TP1: 1.5x–2x RR based on breakout range
8. TP2: Sector index target zone

### Sell Setup:
1. Stock shows LH → LL structure (Dow Downtrend)
2. Sector index in LL-LH structure with RSI < 45 and OBV showing distribution
3. Stock underperforms index (Beta < 1 or % drop > sector in 2 days)
4. Entry below last breakdown candle close
5. SL: Above last LH
6. TP1: Prior support zone
7. TP2: Extension based on sector momentum

---

## 4. CNS/ML/Bot Interaction

### CNS:
- Verifies alignment between stock and sector structure + indicators
- If multiple sector signals occur in conflict, CNS prioritizes:
  - Highest ranked sector in strength table (sector heatmap)
  - OR filters by strategy priority (e.g., gives preference to breakout setups over mean-reversion)
- If sector RSI is 48–52 (neutral):
  - Signal is suspended unless OBV is exceptionally strong
- Logs reasons clearly: “Approved due to Sector Alpha Strength” or “Declined due to Sector Neutrality”

### ML Assignments:
| ML | Role |
|----|------|
| ML1 | Detects Dow structure in both stock and sector |
| ML2 | Tracks OBV, rolling beta, and institutional volume flows |
| ML3 | Flags macroeconomic news/events that might distort sector alignment |
| ML5 | Aggregates confidence: price structure + sector flow + sentiment |
| ML7 | Sizes position using sector volatility, correlation, and weight (larger in stable sectors) |

### Bots:
- **SwingBot:**
  - Avoids signals on earnings release week (checked via earnings API)
  - Prioritizes clean structure + high sector divergence (stock alpha > sector beta)
- **PulseBot:**
  - Rejects signals in sectors where VIX spike > 10% intraday
  - Filters top 3 sectors only for intraday scanning
- **OptionBot:**
  - Uses IV Rank filter > 40
  - Avoids neutral sectors (RSI 48–52)
  - Chooses strike based on expected move derived from sector ATR

---

## 5. UI Dashboard Functions
- Toggle: “Activate Sector Flow Alignment”
- Sector heatmap: Green = trending strong, Red = weak or in distribution
- Signal panel includes:
  - Stock structure
  - Sector classification
  - ML5 confidence score
  - Conflict resolution note (if applicable)

---

## 6. Special Notes & Trading Rules
- Top historically responsive sectors for swing:
  - Nifty IT, Nifty Auto, Nifty FMCG, Nifty Bank
- Avoid entry in sideways market phases where sector RSI = 48–52 and OBV is flat
- Recheck sector direction if stock hits TP1 but stalls (CNS may advise early exit)
- Use for Swing, Intraday, and Option trading only when sector AND stock direction are aligned
- Strategy is auto-disabled if sector-wide choppiness > threshold (measured by ML5 sector confidence < 50)

---

## Verdict:
An institutional-grade sector alignment filter that overlays Dow structure to guide trades toward strong capital flows. Enhances strategy quality when paired with divergence, trap, or range systems.

**Next:** Log 54P – Dow + VWAP Rejection Trap System
