
# PLUS GPT LOG 54G: DOW + RSI COMPRESSION REVERSAL STRATEGY

## Purpose:
To define a momentum-reversal strategy using Dow Theory swing context + RSI compression + breakout logic. This method identifies explosive moves **just after periods of tight range and internal trend conflict**, often used for intraday breakouts and swing entries.

---

## 1. Core Concept Summary
- **Dow Theory** provides structure direction: we identify if price is inside a HH-LH or LL-HL conflict zone
- **RSI Compression** flags when RSI flattens near midpoint (40–60 zone)
- **Breakout Candle** confirms the direction of the explosive release after compression

The strategy captures reversals from **tight coiling zones**, where both price and RSI show indecision — and then break directionally.

---

## 2. Ideal Use Cases
- Intraday range breakouts after chop
- Swing entry after 2–3 tight-range candles (1H/4H)
- Stocks or indices near decision points (e.g. triangle apex or compression wedge)

---

## 3. Entry Criteria

### Long Entry:
- Dow HL sequence holds but HH fails (price compresses between)
- RSI enters 45–55 band for at least 5–7 bars
- Volume slowly decreases during coil
- Breakout bullish candle closes above compression range
- Optional: OBV or VWAP starts rising with breakout

### Short Entry:
- Dow LH holds but LL fails (coiling phase)
- RSI compresses between 45–55 for multiple bars
- Bearish breakout candle closes below range low
- Volume starts rising at breakout

---

## 4. Exit Criteria
- First target: range width projection from breakout
- Trail stop under HLs (for long) or above LHs (for short)
- Exit if RSI diverges from price (e.g. price makes HH, RSI doesn’t)
- Emergency exit if price returns inside compression zone

---

## 5. CNS, ML, BOT Integration

### ML Assignments
- **ML1**: Maps Dow structure and compression zones
- **ML2**: Analyzes RSI bandwidth + slope compression
- **ML6**: Detects fake breakouts + volume reliability
- **ML5**: Aggregates signal strength into Reversal Confidence Score

### CNS Layer
- Confirms compression pattern integrity
- Suppresses trades in news or erratic market context
- Logs breakout strength score (based on RSI slope + volume delta)

### Bot Behavior
- **PulseBot:** Intraday use; enters on compression break
- **SwingBot:** Entry on Daily/4H if RSI flat + volume breakout
- SL/TP set using range width + Dow-defined targets

---

## 6. Trade Style Mapping

### Intraday (PulseBot)
- Chart: 5m/15m
- Ideal during 10:30–1:30pm or 2:15–3:15pm phases
- Entry: Compression break + Dow alignment
- Exit: Range-projected target or time stop

### Swing (SwingBot)
- Chart: 1H/4H/Daily
- Entry: Inside bar pattern or flat RSI at support/resistance
- Exit: Momentum fade or Dow structure reversal

### Options (OptionBot)
- Entry: On breakout with high OBV
- Expiry: Weekly CE/PE on directional bias
- Exit: Opposite breakout or theta decay onset

---

## 7. Special Considerations
- Avoid during earnings/news events
- RSI must compress without spikes (spike = disqualify)
- Works best after long directionless phase

---

**Next Log → 54H: Dow Trend Reversal + Candlestick Trap Strategy**
