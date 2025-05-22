
# Plus GPT Log 56: Intraday System Final Integration Blueprint

## Purpose:
This log serves as the final integration plan to complete the **Intraday Trading System** within the CNS (Central Nervous System) framework. It connects all completed components—strategies, ML layers, CNS roles, execution modes, conflict handling, and watchlist logic—into a single modular, executable system.

---

## 1. Strategy Execution Layer
- **Total Strategies:** 20 (Logged in 49A–49D)
- **Format:** Modular plug-and-play; each has:
  - Entry/exit rules
  - ML1–ML7 mappings
  - CNS conflict logic
  - Auto / Semi-Auto / Manual mode support

- **Grouped by Type:**
  - Scalping (5)
  - Reversal (7)
  - Momentum (5)
  - Smart Money / Spoof / Trap (3)

- **Integration Point:** `strategies/active_strategies.json`

---

## 2. PulseBot Logic Framework
- **Bot Role:** Execute intraday trades for active strategies.
- **Input Sources:**
  - Live market feed (Dhan API, yFinance, Screener)
  - ML real-time insights
  - CNS conflict and regime filter

- **Core Modules:**
  - `strategy_loader.py`
  - `pulse_executor.py`
  - `ml_interface.py`
  - `cns_bridge.py`

- **Modes:**
  - Auto: Executes on signal
  - Semi-Auto: Alerts user; CNS waits for confirmation
  - Manual: Shows only signals; user acts

---

## 3. ML Layer Integration (ML1–ML7)
- **Status:** Assigned in all strategies
- **Final Binding:**
  - ML1: Pattern reader — connects to `chart_scanner.py`
  - ML2: Institutional activity — connects to `orderflow_monitor.py`
  - ML3: News/Sentiment — plugs into `sentiment_filter.py`
  - ML4: Regime checker — integrates with `regime_engine.py`
  - ML5: Confidence engine — computes final score
  - ML6: Trap/Spoof detection — filters out fake signals
  - ML7: Position sizing — calculates capital exposure

- **ML Activation Layer:** CNS calls ML functions at signal validation stage.

---

## 4. CNS Role & Conflict Logic
- **Input:** Multiple strategies can trigger conflicting entries
- **Resolution Flow:**
  - CNS checks ML5 scores, ML6 traps, ML4 regime
  - Cancels weaker signal if conflict
  - Prefers higher-level regime-aligned signal

- **Overrides:**
  - Smart Money alert (ML6) can override all
  - Sentiment Flip (ML3 + GPT) has global priority

- **Modes Controlled by CNS:**
  - Strategy mode switching (Auto, Semi, Manual)
  - Trade approvals
  - Alerts and logs

---

## 5. Watchlist + Universe Filter
- **Logged in:** Log 24 (Smart Universe Filter)
- **Logic Flow:**
  - Pre-market: ML scans for volatility, setups, trap potential
  - CNS builds strategy-specific watchlists
  - PulseBot loads these per strategy

---

## 6. Night Mode (Pre/Post Market Intelligence)
- **Logged in:** Log 25
- **Functions:**
  - After market: MLs run scans
  - Detect overnight gaps, sector pressure, smart money traps
  - Logs stored as JSON for next-day plan

---

## 7. Trade Lifecycle Flow
1. Strategy triggered →
2. ML validations (1–7) →
3. CNS approves/rejects →
4. PulseBot executes →
5. ML7 adjusts size →
6. CNS logs →
7. Alert sent (Auto/Semi/Manual)

---

## 8. Pending Tasks for Execution Phase

| Task                                | Required Log | Status  |
|-------------------------------------|--------------|---------|
| Finalize PulseBot.py code structure | Log 57       | Pending |
| Build Backtest Engine (ML4/ML7)     | Log 58       | Pending |
| Integrate Telegram Alert System     | Log 59       | Pending |
| Connect to CNS UI + Toggle System   | Log 60       | Pending |

---

## Conclusion:
The **Intraday System blueprint is now fully integrated on paper**. Logs 49A–49D provide modular strategies, CNS rules are established, and ML integration is logically defined. The next logs will handle execution layer build-out (PulseBot.py) and real-time testing.

**This completes Plus GPT Log 56.**
