# Pitch Deck Revision Plan: FE571 Final Presentation

## Overview
Restructure the 12-slide presentation into a 18-20 slide deck that is:
- Visual-first (charts/tables on every content slide)
- Concise text (one-liners, no paragraphs)
- Executive-ready (can be printed and understood without presenter)
- Honest about performance while framing strategically

---

## Slide-by-Slide Plan

### SLIDE 1: Title (KEEP - Minor Edit)
**Current:** Statistical Basket Pairs Trading Strategy
**Change:** Add subtitle for context

```
Statistical Basket Pairs Trading Strategy
Volatility Dispersion Mean-Reversion

FE571 | Professor Anshul Sharma | Group 7
Scott Henriquez, Nakul Jadeja, Ayan Mahmood, Akbar Pathan
```

---

### SLIDE 2: Executive Summary (KEEP - Tighten Copy)
**Current:** 6 bullet points, too wordy
**Revised:** 4 bullets max, punchier

```
Executive Summary

• Long/short volatility spread strategy across 4 sector pairs
• Market-neutral design with low SPY correlation (-0.07)
• ML filter tested to improve signal quality
• Result: Solid framework, inconsistent alpha — strategy works as portfolio hedge, not standalone
```

**No visual needed** - this is the "TL;DR" slide

---

### SLIDE 3: The Opportunity (NEW SLIDE)
**Purpose:** Hook the audience with the "why"

```
The Opportunity

[CHART: Simple diagram showing two baskets with volatility lines diverging then converging]

"When volatility between related stocks diverges, it tends to snap back"

• Semiconductor equipment makers vs chip designers
• Integrated oil majors vs refiners
• Temporary dislocations create trading opportunities
```

**One-liner:** Mean-reversion happens 5-7% of the time — we only trade when it's statistically extreme.

---

### SLIDE 4: Basket Construction (KEEP - Add Visual)
**Current:** Table only
**Add:** Simple visual diagram showing Long vs Short baskets

```
Basket Construction

[TABLE - Keep existing 4-pair table]

[VISUAL: Two-column diagram]
LONG BASKET          SHORT BASKET
(Lower Vol)          (Higher Vol)
    ↓                    ↓
Equal-weighted       Equal-weighted

```

**One-liner:** Pairs selected for economic linkage — same sector, different volatility profiles.

---

### SLIDE 5: Signal Generation (KEEP - Simplify)
**Current:** Too much text in entry/exit rules
**Revised:** Make it a visual flow

```
Signal Generation

[FLOW DIAGRAM]
20-Day Rolling Vol → Vol Spread → 120-Day Z-Score → Trade Signal

ENTRY                          EXIT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Z > +2.0  → Short spread      |Z| < 0.5 → Close
Z < -2.0  → Long spread       |Z| > 3.5 → Stop out
VIX > 30  → Stay flat         Loss > 7% → Stop out
```

**One-liner:** We enter on extremes (2σ) and exit when spreads normalize or risk limits hit.

---

### SLIDE 6: ML Enhancement (NEW SLIDE)
**Purpose:** Explain ML addition before showing results

```
Machine Learning Filter

[VISUAL: Simple funnel diagram]
Raw Z-Score Signals (100%) → Random Forest Filter → Filtered Signals (~60%)

8 Features Used:
┌─────────────────────┬─────────────────────┐
│ z-score             │ momentum_5d         │
│ vol_ratio           │ corr_stability      │
│ vix_level           │ days_since_cross    │
│ spread_velocity     │ half_life           │
└─────────────────────┴─────────────────────┘

Walk-Forward Validation: Retrain quarterly, 30-day embargo between train/test
```

**One-liner:** ML acts as a quality filter — only take signals the model thinks will work.

---

### SLIDE 7: Feature Importance (NEW SLIDE)
**Purpose:** Show which features matter

```
What Drives the Model?

[CHART: Horizontal bar chart from v5 - ML Feature Importance]

```

**One-liner:** Z-score and momentum are the strongest predictors — simple features beat complex ones.

**Source:** v5 notebook generates this chart

---

### SLIDE 8: Backtest Setup (NEW SLIDE)
**Purpose:** Establish credibility of backtest methodology

```
Backtest Methodology

Period:        2015-01-01 to 2024-12-31 (10 years)
In-Sample:     2015-2024 (model training)
Out-of-Sample: 2025 YTD (true forward test)

┌────────────────────────────────────────────────┐
│ ✓ Position lagged 1 day (no look-ahead)       │
│ ✓ 30-day embargo between train/test           │
│ ✓ Transaction costs: 5 bps per side           │
│ ✓ Walk-forward quarterly retraining           │
└────────────────────────────────────────────────┘
```

**One-liner:** Backtest is clean — no look-ahead bias, realistic transaction costs.

---

### SLIDE 9: Cumulative Returns (NEW SLIDE - CRITICAL)
**Purpose:** Show the equity curve — most important chart

```
Strategy Performance: Cumulative Returns

[CHART: Cumulative returns line chart from v5 showing all 4 pairs]
[Include vertical line marking train/test split]

```

**One-liner:** Mixed results across pairs — Semiconductors and Tech show promise, Energy and Staples struggle.

**Source:** v5 notebook - cumulative returns chart

---

### SLIDE 10: Drawdown Analysis (NEW SLIDE - CRITICAL)
**Purpose:** Show risk visually

```
Drawdown Profile

[CHART: Drawdown chart from v5 - underwater equity curve]

Max Drawdowns by Pair:
• Semiconductors: -50%
• Energy: -50%
• Tech vs Mega: -26%
• Staples vs Discr: -43%
```

**One-liner:** Significant drawdowns require strong conviction and proper position sizing.

**Source:** v5 notebook - drawdown visualization

---

### SLIDE 11: Performance Table (REVISED FROM CURRENT SLIDE 6)
**Purpose:** Side-by-side ML vs Baseline comparison

```
Performance Comparison: ML vs Baseline

[TABLE]
                    │ BASELINE          │ ML-ENHANCED       │
Pair                │ Sharpe │ MaxDD    │ Sharpe │ MaxDD    │
━━━━━━━━━━━━━━━━━━━━┼────────┼──────────┼────────┼──────────┤
Semiconductors      │ -0.19  │ -50%     │ +0.09  │ -30%     │
Energy              │ +0.01  │ -50%     │ +0.08  │ -50%     │
Tech vs Mega        │ +0.18  │ -26%     │ +0.09  │ -24%     │
Staples vs Discr.   │ -0.34  │ -43%     │ -0.34  │ -35%     │
```

**One-liner:** ML reduces drawdowns but doesn't consistently improve Sharpe — filtering helps risk, not return.

**Source:** v5 notebook - performance_summary.csv

---

### SLIDE 12: Rolling Sharpe (NEW SLIDE)
**Purpose:** Show performance consistency over time

```
Rolling Sharpe Ratio (252-Day Window)

[CHART: Rolling Sharpe line chart from v5]
[Horizontal lines at +1, 0, -1 for reference]

```

**One-liner:** Sharpe fluctuates significantly — strategy has periods of strength and weakness.

**Source:** v5 notebook - rolling Sharpe chart

---

### SLIDE 13: Alpha Analysis (NEW SLIDE)
**Purpose:** Show relationship to benchmark

```
Alpha & Beta vs SPY

[TABLE]
Pair                │ Alpha    │ Beta    │ Corr w/ SPY │
━━━━━━━━━━━━━━━━━━━━┼──────────┼─────────┼─────────────┤
Semiconductors      │ +1.2%    │ -0.02   │ -0.08       │
Energy              │ -2.1%    │ +0.01   │ +0.03       │
Tech vs Mega        │ +0.5%    │ -0.03   │ -0.12       │
Staples vs Discr.   │ -3.5%    │ -0.01   │ -0.05       │
━━━━━━━━━━━━━━━━━━━━┼──────────┼─────────┼─────────────┤
PORTFOLIO           │ -0.89%   │ -0.02   │ -0.07       │
```

**One-liner:** Near-zero beta confirms market neutrality — strategy returns are uncorrelated with SPY.

**Source:** v5 notebook - alpha analysis output

---

### SLIDE 14: Monthly Returns Heatmap (NEW SLIDE)
**Purpose:** Show seasonality and return distribution

```
Monthly Returns Heatmap

[CHART: Heatmap from v5 - months vs years, color-coded returns]

```

**One-liner:** No clear seasonality — returns are spread across different periods.

**Source:** v5 notebook - monthly heatmap

---

### SLIDE 15: Yearly Excess Returns (KEEP - Add Chart)
**Current:** Table only
**Add:** Bar chart showing strategy vs SPY by year

```
Yearly Performance vs SPY

[CHART: Grouped bar chart - Strategy return vs SPY return by year]

Key Insight:
• 2018: Strategy +13% vs SPY -4%  ✓
• 2022: Strategy +16% vs SPY -18% ✓
• 2020: Strategy -40% vs SPY +18% ✗
• 2021: Strategy -25% vs SPY +29% ✗
```

**One-liner:** Strategy outperforms in down markets — potential use as a tail-risk hedge.

---

### SLIDE 16: Correlation Matrix (NEW SLIDE)
**Purpose:** Show diversification benefit

```
Strategy Diversification

[CHART: Correlation heatmap from v5 - 4x4 matrix of pair correlations]

Average Pairwise Correlation: 0.03
```

**One-liner:** Low correlation between pairs means combining them reduces overall portfolio risk.

**Source:** v5 notebook - strategy correlation matrix

---

### SLIDE 17: Risk Summary (REVISED FROM CURRENT SLIDE 7)
**Purpose:** Consolidate risk metrics

```
Risk Profile

[TABLE]
Metric              │ Value           │ Interpretation            │
━━━━━━━━━━━━━━━━━━━━┼─────────────────┼───────────────────────────┤
Max Drawdown        │ -26% to -50%    │ Significant capital risk  │
VaR (95%)           │ -1.0% to -1.7%  │ Daily loss expectation    │
CVaR (95%)          │ -1.6% to -2.9%  │ Tail risk in worst days   │
Win Rate            │ 48-52%          │ Slightly below coin flip  │
Avg Holding Period  │ 15-30 days      │ Medium-term positions     │
```

**One-liner:** This is a low win-rate, high-variance strategy — position sizing is critical.

---

### SLIDE 18: What We Learned (REVISED FROM CURRENT SLIDE 10)
**Purpose:** Show intellectual rigor

```
Fixes & Lessons Learned

What We Fixed:                     What We Learned:
━━━━━━━━━━━━━━━━━━━━━━━           ━━━━━━━━━━━━━━━━━━━━━━━━
✓ Removed look-ahead bias          • 8 features beat 40
✓ Added 30-day train/test embargo  • Spread only mean-reverts 5-7% of time
✓ Corrected transaction costs      • VIX regime matters
✓ Implemented 3 stop-loss rules    • Alpha is hard to find
```

**One-liner:** Proper backtesting revealed our initial results were inflated — honesty improved the strategy.

---

### SLIDE 19: Conclusion (REVISED FROM CURRENT SLIDE 11)
**Purpose:** Clear investment thesis

```
Investment Thesis

WHAT WORKED                        WHAT DIDN'T
━━━━━━━━━━━━━━━━━━━━━━            ━━━━━━━━━━━━━━━━━━━━━━
✓ Market-neutral (β ≈ 0)          ✗ No consistent alpha
✓ Low SPY correlation             ✗ Large drawdowns
✓ Stop-losses limit tail risk     ✗ Underperforms in bull markets
✓ Outperforms in down markets     ✗ Low win rate

RECOMMENDATION:
This strategy is best suited as a PORTFOLIO HEDGE, not a standalone alpha source.
Allocate 5-10% of portfolio for downside protection.
```

**One-liner:** Proper framework, proper risk controls — but alpha is elusive in efficient markets.

---

### SLIDE 20: Questions (KEEP)
**Current:** Fine as-is

```
Questions?

GitHub: github.com/Ayan-Mahmood/QuantHFStrat
```

---

## Charts to Export from v5 Notebook

Run the v5 notebook and save these figures:

| Chart | Slide | Filename |
|-------|-------|----------|
| Cumulative Returns | 9 | cumulative_returns.png |
| Drawdown | 10 | drawdown_chart.png |
| Rolling Sharpe | 12 | rolling_sharpe.png |
| Feature Importance | 7 | feature_importance.png |
| Monthly Heatmap | 14 | monthly_heatmap.png |
| Correlation Matrix | 16 | correlation_matrix.png |
| Cumulative Alpha | 13 | cumulative_alpha.png |

---

## Summary of Changes

| Current Slides | Action | New Slide # |
|----------------|--------|-------------|
| 1. Title | Keep + minor edit | 1 |
| 2. Exec Summary | Tighten copy | 2 |
| 3. Economic Rationale | Merge into new "Opportunity" | 3 |
| 4. Basket Construction | Keep + add visual | 4 |
| 5. Signal Generation | Simplify to flow | 5 |
| — | NEW: ML Enhancement | 6 |
| — | NEW: Feature Importance | 7 |
| — | NEW: Backtest Setup | 8 |
| — | NEW: Cumulative Returns | 9 |
| — | NEW: Drawdown | 10 |
| 6. Backtest Performance | Revise to ML vs Baseline | 11 |
| — | NEW: Rolling Sharpe | 12 |
| — | NEW: Alpha Analysis | 13 |
| — | NEW: Monthly Heatmap | 14 |
| 8. Yearly Excess Returns | Keep + add chart | 15 |
| 9. Cross-correlation | Move to Correlation Matrix | 16 |
| 7. Risk & Tail Behavior | Revise to Risk Summary | 17 |
| 10. Fixes & Improvements | Revise to Lessons Learned | 18 |
| 11. Conclusion | Revise with thesis | 19 |
| 12. Questions | Keep | 20 |

---

## Design Guidelines

1. **One visual per slide** (chart, table, or diagram)
2. **One-liner interpretation** below each visual
3. **Max 4-5 bullet points** if no visual
4. **Consistent colors**: Use Stevens red (#9D1535) for emphasis
5. **No paragraphs** — everything scannable
6. **Source data** from v5 notebook outputs

---

## Files to Reference

- `/Users/akbarpathan/Desktop/Dev/QuantHFStrat/backtesting/v5_Enhanced_Visualization.ipynb` - All charts
- `/Users/akbarpathan/Desktop/Dev/QuantHFStrat/backtesting/performance_summary.csv` - Metrics data
- `/Users/akbarpathan/Desktop/Dev/QuantHFStrat/reports/Backtest_Integrity_Audit_v4.md` - Methodology validation
