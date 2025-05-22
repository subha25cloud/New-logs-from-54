# Plus GPT Log 57: PulseBot Execution Code Blueprint

## Purpose:
To define the complete Python-based architecture of **PulseBot**, the CNS-controlled intraday trading bot. This blueprint includes all code modules, file structure, communication protocols, and real-time trade flow logic needed to make PulseBot a live, modular, and executable bot that integrates with strategy logic, ML outputs, and CNS decisions.

---

## 1. Project Directory Structure

pulsebot/
├── main.py                         # Master trigger file (CNS starts here)
├── config/
│   └── api_keys.json              # Token, client ID, credentials
├── strategies/
│   └── strategy_loader.py        # Loads active JSON strategy files
├── executor/
│   ├── pulse_executor.py         # Order management + signal processor
│   ├── position_manager.py       # Entry, exit, SL, trailing stop
│   └── sizing_engine.py          # ML7-based position sizer
├── ml/
│   ├── ml_router.py              # ML1–ML7 API connector
│   ├── sentiment_filter.py       # ML3-specific NLP logic
│   └── regime_engine.py          # ML4-based market regime controller
├── watcher/
│   ├── universe_filter.py        # Pre-market ML-based stock filter (Log 24)
│   └── signal_detector.py        # Signal scanner per active strategy
├── bridge/
│   └── cns_bridge.py             # Communication between CNS ↔ PulseBot
├── ui/
│   └── alert_dispatcher.py       # Telegram + voice call alerts (Log 59)
├── data/
│   └── logs/                     # Trade logs, backtest results, JSON state
└── utils/
    ├── time_utils.py
    ├── vwap_calculator.py
    └── volume_profile.py

---

## 2. Core Logic Flow

1. `main.py` booted by CNS â†’
2. Loads active strategies (`strategy_loader.py`)
3. Universe Filter creates daily stock list (`universe_filter.py`)
4. Live market data flows in
5. Signal detector runs on selected stocks per strategy
6. ML1â€“ML7 validators score the signal
7. `cns_bridge.py` asks CNS for trade permission
8. If approved, `pulse_executor.py` sends order
9. `position_manager.py` monitors trade
10. `sizing_engine.py` adjusts position sizing based on ML7
11. Alerts dispatched via `alert_dispatcher.py`

---

## 3. Communication Protocols

- **CNS â†” PulseBot:** Socket or API call using `cns_bridge.py`
- **PulseBot â†” MLs:** ML model endpoints via `ml_router.py`
- **PulseBot â†” Dhan API:** Order/positions via REST/Websocket
- **PulseBot â†” User Alerts:** Telegram bot and/or Twilio API
- **PulseBot â†” GPT (Fallback Loop):**
  - If CNS, ML, and bot layers cannot resolve an issue, PulseBot opens a secure backchannel to GPT for direct diagnostic assistance.
  - This fallback is **always enabled by default** for **intraday** mode.

---

## 4. PulseBot Modes

- **Auto Mode:** CNS approves + bot executes immediately (**default for intraday**)
- **Semi-Auto:** CNS alerts user and waits for confirmation
- **Manual Mode:** CNS only displays signals; user executes manually (disabled by default)

---

## 5. Strategy Activation

- Controlled via JSON toggle in `/strategies/active_strategies.json`
```json
{
  "VWAP Bounce": true,
  "EMA Pullback": false,
  "Gap Reversal": true
}
```
- `strategy_loader.py` parses this file and loads only enabled logic

---

## 6. ML Integration Sync

- ML1: Pattern confirmation (from signal_detector)
- ML2: Institutional strength (via orderflow_monitor)
- ML3: Sentiment risk (via sentiment_filter)
- ML4: Market regime validation
- ML5: Final confidence score
- ML6: Spoof/trap rejection logic
- ML7: Position size calculator

---

## 7. Error Handling & Fail-Safes

- All orders wrapped in try/except
- Real-time logging in `/data/logs/`
- Emergency exit trigger if:
  - CNS flags systemic risk
  - ML3 signals high-impact news
  - Order rejected or slippage detected
  - GPT fallback loop engaged for rare decision-layer breakdowns

---

## 8. Upcoming Enhancements (Future Logs)

| Feature                                 | Log Ref     | Status  |
|-----------------------------------------|-------------|---------|
| Backtesting Engine                      | Log 58      | Complete |
| Telegram Alert System                   | Log 59      | Pending |
| CNS UI Sync                             | Log 60      | Pending |
| Strategy Performance Tracker            | Log 61      | Planned |

---

## Conclusion

This blueprint defines the complete execution structure of **PulseBot**, including real-time execution logic, modular folder design, ML coordination, CNS communication, GPT fallback loop, and live strategy deployment. Once this folder is coded and connected, PulseBot becomes the active executor of all intraday logic.

**End of Plus GPT Log 57**
