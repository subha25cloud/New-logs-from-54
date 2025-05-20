
# PLUS GPT LOG 54I: DOW + MACD + RANGE EXHAUSTION REVERSAL STRATEGY

## Purpose:
To define a reversal strategy combining **Dow Theory structure**, **MACD histogram contraction**, and **range exhaustion detection**. This hybrid system identifies turning points when a strong directional move starts losing steam after a full range cycle.

---

## 1. Core Logic Overview
This strategy detects fading trend moves by aligning:
- **Dow Theory:** Detects when a trend structure starts breaking (e.g., HH → LH or LL → HL)
- **MACD Histogram:** Shows momentum loss (shrinking bars near 0 line)
- **Range Exhaustion:** The move has covered its statistical average range (ADR or intraday VWAP bands)

It captures **momentum collapse trades** at the tail end of trends, especially after long moves.

---

## 2. Ideal Use Case
- Index futures after extended trending sessions
- Swing stocks that have moved >2× ATR in few bars
- Spotting entry into reversal trades with low risk, high reward

---

## 3. Entry Criteria

### Long Reversal:
- Price made LL but fails to continue
- Dow shows early HL attempt
- MACD histogram flips from strong negative to zero zone
- Price hits lower extreme of ADR or VWAP deviation band

### Short Reversal:
- Price made HH but fails to follow through
- Dow prints early LH pattern
- MACD histogram compresses and begins to turn down
- Price at upper ADR or VWAP resistance zone

**Optional Add-ons:**
- RSI Divergence or OBV stalling can boost confidence

---

## 4. Exit Logic
- TP1 at midpoint of last swing (mean reversion)
- TP2 at opposite VWAP band or recent SR zone
- SL just beyond most recent extreme (HH or LL)
- Emergency exit: if MACD momentum flips back toward trend

---

## 5. ML–CNS–Bot Framework

### MLs
- **ML1:** Confirms Dow structure change (HH → LH or LL → HL)
- **ML2:** Analyzes MACD slope and histogram compressions
- **ML4:** Confirms exhaustion using ADR % or VWAP band status
- **ML5:** Confidence calculator – needs structure + momentum fade + range criteria

### CNS Behavior
- Filters trades that appear too early (before Dow confirms structural change)
- Validates only when exhaustion aligns with high TF context (ML4)
- Assigns a “Momentum Fade Risk Score” to each signal
- Suppresses if news/fundamental overrides detected (via ML3)

### Bot Actions
- **PulseBot:** Intraday reversal trades at range edges
- **SwingBot:** Reversal entries after strong daily candles
- **PositionBot:** Uses only if reversal confirmed across two timeframes (e.g. daily + weekly)

---

## 6. Trading Style Mapping

### Intraday
- Chart: 5m/15m
- Use: Fade move after extended trend leg
- SL tight beyond recent wick, TP near VWAP center

### Swing
- Chart: 1H/4H/Daily
- Use: After 2–3 wide range bars with fading MACD
- TP/SL based on Fibs or prior structure

### Positional
- Use: Rarely – only when multi-day exhaustion + Dow reversal confirmed
- Use RSI/volume divergence to validate

---

## 7. Notes
- Avoid in sideways range (MACD will whipsaw)
- Strongest when Dow + MACD + range all signal reversal
- Pairs well with **volatility spike filters** (ML6 can assist)

---

**Next Strategy: Log 54J – Dow + Smart Money Divergence Structure Strategy (Final in Dow Series)**
