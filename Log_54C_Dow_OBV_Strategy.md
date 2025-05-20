# PLUS GPT LOG 54C: DOW + OBV MOMENTUM STRATEGY

## Purpose
This log defines a strategy that combines **Dow Theory market structure validation** with **OBV-based momentum surges** to create powerful trend-aligned entry signals. It is designed for **swing trading** and **options breakout entries**, using volume and structure confluence to enhance decision-making accuracy.

---

## Strategy Name: Dow + OBV Momentum Breakout

### Best Suited For:
- **Swing Trades** with strong directional moves
- **Option Breakout Entry** where volume confirms strength
- **Trend Continuation** trades filtered through Dow logic

---

## Entry Logic:
1. **Dow Structure Validation**:
   - Confirm trend: e.g., LL → HL → HH = Bullish
   - Reject trades if Dow swing fails (e.g., HH → LH)

2. **OBV Confirmation**:
   - OBV should break recent horizontal resistance (volume breakout)
   - Combine with breakout candle or compression breakout

3. **Volume Ratio Filter**:
   - Current OBV bar > 1.5× average OBV of last 5 bars

---

## Exit Logic:
- Exit if OBV diverges (new price high, OBV flat or falling)
- Exit if Dow trend collapses (HH → LH → LL)
- Trailing SL below Dow-defined HL or OBV pullback level

---

## CNS–ML–Bot Integration

### ML Integration:
- **ML1**: Tracks Dow structure shifts in real time
- **ML2**: Detects OBV slope, momentum surges, and resistance breaks
- **ML5**: Combines OBV + Dow into confidence score (TAS score)
- **ML7**: Adjusts position size based on volume pressure

### Bot Behavior:
- **SwingBot**: Default executor for this strategy
- **OptionBot**: Enters only when OBV + Dow both align
- PulseBot ignores this unless used in special mode

### CNS Role:
- Filters entries through Dow + OBV layer
- Logs OBV shift zone, Dow state, and score
- Blocks trade if either layer shows conflict

---

## Application by Trading Type

### A. Swing Trading:
- **Chart**: 1h or Daily
- **Entry**: Dow HL→HH confirmed + OBV breakout zone
- **Exit**: OBV failure + HL breakdown

### B. Options (Momentum Entry):
- **Chart**: 15m or 1h
- **Entry**: OBV breakout + Dow trap (e.g., LL→HL→HH)
- **Exit**: OBV reversal or trap break

---

## Conflict Avoidance Rules:
- If OBV shows strength but Dow shows LH→LL, cancel trade
- If Dow is bullish but OBV fails volume confirmation, skip
- CNS logs mismatch and suggests alternative entry zone
- TAS (Trend Alignment Score) < 60% = auto-reject

---

## Special Notes:
- Works best with trending instruments (BankNifty, TATA Motors)
- Avoid in news-heavy zones or flat OBV zones
- Can be combined with Fibonacci or Price Action for high-conviction

---

## Visualization:
- Dow swing labels shown on chart (HH, HL, etc.)
- OBV breakout zone highlighted
- TAS score shown per instrument in dashboard

---

## Final Verdict:
Dow + OBV synergy acts as a **trend continuation filter** with confirmation power. It avoids false breakouts and gives early entry during valid momentum surges.

Next module: **Log 54D – Dow + Inside Bar Compression Strategy**
