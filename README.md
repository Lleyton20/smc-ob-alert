# Magama SMC Order Block Alert

A TradingView indicator, written in Pine Script v5, that detects market structure shifts, marks order blocks, and alerts when price returns to one.

The idea is simple: instead of watching charts all day waiting for price to revisit a zone, let the script watch and notify you.

**Repo contents:** `magama_smc_ob_alert.pine` — a single Pine Script indicator, ~N lines. That's the whole project.

---

## What it does

**Market structure.** Tracks swing highs and lows to classify the current structure as higher-high/higher-low, lower-high/lower-low, or neither. From that it flags two events:

- **BOS (Break of Structure)** — price breaks the prior swing point in the direction of trend. Continuation signal.
- **CHoCH (Change of Character)** — price breaks the prior swing point against the trend. Possible reversal.

**Order blocks.** On a structure break, the script marks the last opposing candle before the impulse move as an order block — a bullish (demand) or bearish (supply) zone — and draws it on the chart.

**Alerts.** Once a zone is drawn, the script watches for price to return to it. When price re-enters, a TradingView alert fires. TradingView handles delivery from there (desktop, mobile, email, browser).

```
swing detection → BOS / CHoCH → mark order block → watch for retest → alert
```

---

## Install

1. Open TradingView → Pine Editor
2. Paste the contents of `magama_smc_ob_alert.pine`
3. Save, then "Add to chart"
4. Right-click chart → Add alert → select this indicator as the condition

---

## Inputs

<!-- TODO: fill this from the actual `input.*` calls in the script.
     One row per input: what it controls and what the default is.
     If a reviewer can't tell how to configure it, the README isn't done. -->

| Input | Default | What it does |
|---|---|---|
| | | |

---

## Known limitations

Worth being upfront about these — they're the honest state of the project, not a roadmap.

- **No backtest.** I haven't measured hit rate or expectancy. The indicator identifies zones; it makes no claim about whether trading them is profitable.
- **Swing detection is lookback-based**, so structure points confirm only after the lookback window closes. Signals are not instantaneous.
- **Repainting:** <!-- TODO: state plainly whether zones can move or disappear after the fact. If you haven't checked, check — this is the first thing anyone experienced will ask. -->
- **Single timeframe.** No multi-timeframe confluence.
- **Order block selection is heuristic** — last opposing candle before the impulse. Other definitions exist; this one is a choice, not a standard.

---

## Ideas for later

Fair value gap detection · liquidity sweep detection · multi-timeframe confluence · a backtest harness to actually measure whether the zones mean anything.

---

## Disclaimer

Educational and analytical use only. This is not trading advice and carries no performance claim. Trading involves substantial risk of loss.                    ▼
