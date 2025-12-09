# QuantHFStrat: The Story of Our Project

## FE 571: Efficiently Inefficient Markets | Stevens Institute of Technology
### Group 7 Final Project

---

## The Big Idea

We built a market-neutral trading strategy that exploits temporary mispricings between related stock baskets. When volatility between two economically-linked groups of stocks gets out of whack, we bet it will return to normal.

**Simple version:** If semiconductor equipment makers suddenly become way more volatile than chip designers, history says that gap will close. We trade that.

---

## Our Journey

### Phase 1: The Baseline Strategy

We started with a straightforward approach:
- Pick 4 pairs of related stock baskets (semiconductors, energy, tech, consumer)
- Track the volatility difference between each pair
- When that difference gets extreme (2 standard deviations), bet on mean-reversion
- Exit when it normalizes

**What we found:**
- The idea made economic sense
- But raw performance was underwhelming
- High drawdowns, inconsistent returns

---

### Phase 2: Adding Machine Learning

We thought: "Can ML help us pick better entry points?"

**What we added:**
- Random Forest classifier to filter signals
- 8 carefully chosen features (z-score, momentum, VIX, correlation, etc.)
- Walk-forward validation to avoid overfitting
- Quarterly model retraining

**Key insight:** Less is more. We started with 40+ features but found 8 simple ones worked better.

---

### Phase 3: The Code Audit (Critical!)

Here's where it got interesting. We did a full code review and found serious problems.

**Issues discovered in v3:**

| Problem | Impact |
|---------|--------|
| Return timing error | Positions used same-day returns (impossible in practice) |
| ML target leakage | Training labels used future data |
| Transaction costs 4x | Math error quadrupled costs |

**The fix:**
- v4 corrected all issues
- Added 30-day embargo between train/test
- Proper `shift(1)` for position lag
- Clean transaction cost formula

**Lesson learned:** Always audit your backtest. Look-ahead bias can hide everywhere.

---

### Phase 4: Enhanced Visualization (v5)

For the final presentation, we:
- Applied Stevens Institute branding (maroon and gray)
- Added alpha/excess return analysis vs SPY
- Created rolling Sharpe charts
- Built monthly returns heatmaps
- Visualized feature importance

---

## What Worked

- **Market-neutral design** - Low correlation with SPY
- **Walk-forward ML** - No look-ahead bias
- **Simple features** - Avoided overfitting
- **Stop-losses** - Z-score, PnL, and VIX stops protected capital

## What Didn't Work

- **High correlations within baskets** - Limited diversification benefit
- **Intermittent stationarity** - Spread only mean-reverts ~5-7% of the time
- **Challenging market conditions** - Strategy struggled in trending markets

---

## Key Metrics (Final Strategy)

| Metric | Value |
|--------|-------|
| Sharpe Ratio | ~0.2-0.5 (pair dependent) |
| Max Drawdown | -25% to -50% |
| Win Rate | ~48-52% |
| Correlation with SPY | Low (<0.3) |

---

## Technical Stack

- **Language:** Python 3
- **Data:** Yahoo Finance (yfinance)
- **ML:** scikit-learn (Random Forest)
- **Stats:** statsmodels, scipy
- **Visualization:** matplotlib, seaborn

---

## Files in This Repository

```
backtesting/
├── v1_Volatility_Dispersion_Baseline.ipynb      # Original strategy
├── v2_Volatility_Dispersion_ML_Enhanced.ipynb   # First ML attempt
├── v3_Improved_Basket_Pair_Trading_Strategy.ipynb  # Has bugs (audit revealed)
├── v4_Volatility_Dispersion_ML_Enhanced_V2.ipynb   # Fixed version
└── v5_Enhanced_Visualization.ipynb               # Final with Stevens branding

reports/
├── Executive_Report_v1.md           # Performance summary
├── Repository_Structure_Report.md   # Codebase guide
├── Backtest_Integrity_Audit_v3.md   # v3 bug report
├── Backtest_Integrity_Audit_v4.md   # v4 verification
└── Project_Story.md                 # This file
```

---

## Lessons for Future Projects

1. **Audit your backtest** - Look-ahead bias is silent and deadly
2. **Start simple** - 8 features beat 40
3. **Use embargo periods** - Gap between training and testing data
4. **Document everything** - Future you will thank present you
5. **Version your notebooks** - Each iteration tells a story

---

## Team

**Group 7 | Stevens Institute of Technology | Fall 2024**

---

*This strategy is for educational purposes. Past performance does not guarantee future results.*
