# PulseBot Intraday Backtesting Engine – Blueprint

## Purpose:
Design and build a full-featured backtesting module inside PulseBot to simulate intraday strategy logic under real-world constraints including ML scoring, CNS decision-making, and multi-strategy conflicts.

---

## 1. Data Requirements
- **1-Minute Historical Data**
  - OHLCV per symbol
  - Source: yFinance, Dhan API, CSV
- **Strategy Rules File**
  - Stored as JSON for modular parsing
- **Market Regime Context**
  - Optional index data for environment detection (ML4 emulation)

---

## 2. Directory Structure

```
pulsebot/backtest/
├── backtest_engine.py
├── strategy_simulator.py
├── regime_simulator.py
├── sizing_replayer.py
├── conflict_tester.py
├── report_generator.py
└── logs/
```

---

## 3. Simulation Flow

1. Load symbol & time range
2. Process every 1-min candle
3. Trigger strategy rules
4. Evaluate ML1–ML7 scores
5. CNS approves/rejects
6. Simulated trade execution
7. Result logging

---

## 4. Conflict Resolution Logic (CNS Replica)

- Prioritize:
  1. Smart Money logic (ML6)
  2. Sentiment Reversal (ML3)
  3. Higher ML5 score
  4. Breakouts > Mean Reversion
- All decisions routed via `conflict_tester.py`

---

## 5. ML Simulation Per Trade

| ML | Function Emulated                         |
|----|-------------------------------------------|
| ML1 | Pattern check from price + structure     |
| ML2 | Volume or block order logic              |
| ML3 | Time-based news exclusions               |
| ML4 | ATR or volatility regime check           |
| ML5 | Signal confidence (scored)               |
| ML6 | Trap/spoof detection based on history    |
| ML7 | Volatility-adjusted sizing calculation   |

---

## 6. Sample Trade Log Output

```json
{
  "symbol": "NIFTY",
  "strategy": "Gap Reversal",
  "entry_time": "09:30",
  "exit_time": "09:35",
  "entry_price": 22040,
  "exit_price": 22080,
  "status": "TP Hit",
  "ml_scores": {"ML1": 0.9, "ML5": 0.87},
  "cns_decision": "Approved",
  "conflict": false
}
```

---

## 7. Final Report Generator

- Win rate, loss rate
- Avg R:R
- ML5 vs outcome correlation
- Max drawdown
- Conflicted vs clean trade success

---

## 8. Optional UI Layer

- Strategy toggle
- Period selector
- Batch symbol run
- Graphical curve view (matplotlib)

---

## Conclusion:

The PulseBot Backtesting Engine simulates all real-time trading logic and CNS oversight. It allows dry-run validation of each strategy, enabling performance tracking and conflict-testing before live deployment.

**End of Log 58**