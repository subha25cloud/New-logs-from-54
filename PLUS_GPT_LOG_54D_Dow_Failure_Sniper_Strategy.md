
# PLUS GPT LOG 54D: DOW FAILURE SNIPER STRATEGY

## Purpose:
To define a reversal strategy based on Dow Theory failure patterns (e.g., failed HH, HL, LL, LH), designed to catch early trend reversals or breakdown traps.

---

## Use Cases:
- Intraday scalping during sudden trend failure
- Swing trade reversals post false breakout
- Option buying (PE/CE) on early collapse or flip

---

## Strategy Logic (Core):
- Detects failure of a Dow swing structure:
  - e.g., HH → HL → fails to make new HH → forms LH = sign of reversal
  - e.g., LL → LH → fails to make new LL → forms HL = base for reversal

- Confirms structure collapse using:
  - Volume spike (ML6)
  - OBV rejection or divergence
  - RSI failure divergence (ML2)
  - Reversal candle (engulfing, pin bar)

---

## Entry Criteria:

### Long Entry (Reversal from Downtrend):
- Price forms HL instead of new LL
- Volume surge confirms buyer interest
- RSI divergence + bullish engulfing or pin bar
- OBV starts rising
- Dow fails to break previous LL

### Short Entry (Reversal from Uptrend):
- Price forms LH instead of new HH
- Bearish engulfing + volume trap
- OBV flattening or falling
- Dow fails to break HH
- Trap detection (ML6) active

---

## Exit Criteria:

- Partial exit at major previous HL/LH
- Full exit at structural reversal confirmation (opposite HH or LL)
- Stop-loss below/above failed swing point
- Trailing stop via Supertrend or fixed Renko brick

---

## Trading Style Breakdown

### A. Intraday (PulseBot)
- **Chart:** 5m Renko + Volume + RSI
- **Entry:** On Dow failure + candle pattern + OBV divergence
- **Exit:** Opposite Renko brick or pullback zone
- **Bot Behavior:** Only enter if ML6 confirms trap + ML2 RSI diverges
- **MLs:** ML1 (Dow), ML2 (RSI), ML6 (Trap), ML5 (score)
- **CNS:** Confirms Dow structure break, logs transition

### B. Swing (SwingBot)
- **Chart:** 15m/1h candle + OBV
- **Entry:** Confirm HL → HH failure (for short), or LL → HL (for long)
- **Exit:** Upon breakdown confirmation or retrace to failed zone
- **Bot Behavior:** Slower entry; requires ML1+ML2+ML6 combo trigger
- **CNS:** Delays execution if swing levels not clean
- **MLs:** ML1, ML2, ML5

### C. Options (OptionBot)
- **Chart:** 5m + VIX overlay + OBV
- **Entry:** Enter PE/CE on failure with OBV + VIX spike
- **Exit:** Time-based or breakdown threshold
- **Bot Behavior:** Size adjusts based on structure confidence
- **MLs:** ML1, ML6, ML7
- **CNS:** Blocks re-entry if same failure seen within 20 mins

---

## CNS–ML–Bot Integration

- **ML1:** Detects Dow pattern failure: HH fails to form → structure reversal
- **ML2:** Confirms divergence (price vs momentum)
- **ML6:** Flags fakeouts or traps
- **ML7:** Adjusts lot size if trap strength is high
- **CNS:** Logs Dow shift, assigns reverse-entry zone
- **Bots:** Only act after ML1 + ML2 + ML6 alignment

---

## Special Notes:
- Avoid if Dow structure is not clean (e.g., choppy overlapping bars)
- Disable strategy if 2 consecutive failures misfire (confidence flag drops)
- CNS logs performance after each session to retrain ML1’s pattern memory

---

## Strategy Classification:
- **Type:** Reversal + Trap Sniping
- **Risk Level:** Medium to High
- **Best Market:** Index options, strong movers (Reliance, HDFC, Gold ETF)
- **Execution Mode:** Semi-auto preferred

---

## Log Ref Tag:
`PLUS-GPT-LOG-54D`
