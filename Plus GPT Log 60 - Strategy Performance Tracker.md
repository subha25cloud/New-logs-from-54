# Plus GPT Log 60: Strategy Performance Tracker Engine (PulseBot)

## Purpose:
To build a self-updating engine that evaluates the real-world performance of each active intraday strategy in PulseBot. It monitors trade outcomes, calculates metrics like win rate, R:R ratio, ML5 reliability, false-positive conflicts, and creates a data layer for CNS optimization, daily reporting, and visual dashboards.

---

## 1. File & Directory Structure
```
pulsebot/performance/
├── tracker_engine.py         # Master module: tracks and updates all stats
├── metrics_calculator.py     # R:R, win%, drawdown, profit factor, score
├── ml5_correlation.py        # Analyzes ML5 accuracy vs real outcomes
├── conflict_analysis.py      # Logs blocked trades, measures false conflict rate
├── strategy_stats.json       # Live, updating snapshot of each strategy’s performance
└── history/
    └── daily_logs/           # JSON logs of daily performance data
```

---

## 2. Trade Record Template
```json
{
  "symbol": "BANKNIFTY",
  "strategy": "VWAP Bounce",
  "entry_price": 44125,
  "exit_price": 44170,
  "status": "TP Hit",
  "pnl": 500,
  "r_ratio": 1.2,
  "ml5_score": 0.89,
  "duration": "5min",
  "conflict_blocked": false
}
```

---

## 3. Metrics Tracked Per Strategy
- Total Trades
- Win Rate (%)
- Average R:R
- Max Drawdown
- Profit Factor (Total profit / Total loss)
- Average Holding Time
- ML5 Signal Accuracy (confidence vs reality)
- CNS Conflict Resolution Rate
- False Suppression % (blocked trades that would have hit TP)

---

## 4. Calculation Logic (`metrics_calculator.py`)
```python
win_rate = wins / total_trades
avg_rr = sum(rr_ratios) / len(rr_ratios)
profit_factor = total_gains / total_losses
ml5_accuracy = ml5_tp_count / ml5_high_conf_count
false_conflict_rate = tp_after_block / total_conflicts
```

---

## 5. ML5 vs Outcome Correlation (`ml5_correlation.py`)
- Tracks accuracy of high ML5 signals
- Compares actual trade results to ML5 prediction
- Flags signal anomalies (e.g. ML5 > 0.85 but SL hit)
- Feeds quality score back to CNS for real-time confidence tuning

---

## 6. CNS Feedback Hooks
- **Dynamic Strategy Control:**
  - Disable logic if win rate < 30% after 20 trades
  - Prioritize if ML5 reliability > 90% + Profit Factor > 1.5
- **Daily Weight Update:**
  - CNS learns which strategy is working under current regime
- **Blocked Trade Review:**
  - CNS rechecks trades it skipped to learn from mistake rate

---

## 7. Sample Summary Alert (EOD)
```markdown
**[STRATEGY SCOREBOARD - EOD]**
1. VWAP Bounce: ✅ 5/6 | Win%: 83% | R:R: 1.6 | ML5 Acc: 91%
2. RSI Divergence: ❌ 2/5 | Win%: 40% | R:R: 0.9 | Conflicts: 2
3. Smart Money Reversal: ✅ 3/3 | Win%: 100% | R:R: 2.1
```

---

## 8. History Logs (JSON)
- Daily file: `YYYY-MM-DD_performance.json`
- Includes:
  - Symbol, strategy, result
  - P&L, ML5 score, CNS block/reason
  - R:R, drawdown, time held

---

## 9. UI Dashboard Support (Optional)
- Renders:
  - Green/red bar per strategy
  - Rolling 5-day win rate
  - Sortable table by ML5 accuracy, win%, conflict ratio
- Backend JSON: strategy_stats.json powers display layer

---

## 10. CNS + GPT Review Logic (Optional Fallback)
- If strategy drops below all performance thresholds:
  - CNS sends to GPT for review (explanation, suggestions)
  - GPT suggests:
    - Logic refinements
    - SL/TP rule changes
    - ML or regime filters to tighten

---

## Conclusion:
This Performance Tracker makes PulseBot self-monitoring. It turns every intraday signal into a measurable, improvable action, closing the feedback loop for CNS to evolve, optimize, and debug its own decisions.

**End of Plus GPT Log 60**