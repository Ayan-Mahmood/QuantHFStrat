# Repository Structure Report: QuantHFStrat

## Overview

This repository contains research for **FE571: Quantitative Hedge Fund Trading Strategies** (Group 7 Final Project). The project implements volatility dispersion trading strategies with progressive enhancements.

---

## File Inventory

### Code Files (Jupyter Notebooks)

| File | Lines | Size | Purpose |
|------|-------|------|---------|
| `Volatility Dispersion - Statistical Basket Pairs Trading Strategy.ipynb` | 782 | 991 KB | **BASELINE** - Original implementation |
| `Volatility_Dispersion_ML_Enhanced.ipynb` | 666 | 1.0 MB | **ENHANCED** - Adds ML layer to baseline |
| `Improved_Basket_Pair_Trading_Strategy.ipynb` | 1,954 | 684 KB | **COMPREHENSIVE** - Most complete version |

### Documentation Files

| File | Size | Purpose |
|------|------|---------|
| `Exec Comparison Summary.pdf` | 1.8 MB | Performance comparison report |
| `ML Enhanced Strategy Comparison.pdf` | 2.9 MB | ML enhancement analysis |
| `README.md` | 95 bytes | Minimal project description |
| `LICENSE` | - | MIT License (Ayan Mahmood) |

---

## Code Evolution & Relationships

### The Three Notebooks Explained

```
PROGRESSION:

  [1] BASELINE                [2] ML-ENHANCED              [3] COMPREHENSIVE
  (Original Strategy)    -->  (Adds ML Filter)    -->     (Full Analysis)

  - Basic vol spread          - Random Forest              - Everything from 1 & 2
  - Fixed thresholds          - 40+ features               - Stationarity testing
  - Simple backtest           - Walk-forward validation    - Half-life analysis
  - Performance metrics       - VIX regime adaptation      - Performance attribution
                              - Sharpe comparison          - Yearly excess returns
                                                           - Correlation analysis
```

### Detailed Breakdown

#### 1. `Volatility Dispersion - Statistical Basket Pairs Trading Strategy.ipynb`
**Role:** BASELINE / ORIGINAL

This is the **foundational implementation** with:
- Equal-weighted basket construction
- 20-day rolling volatility calculation
- 120-day z-score window
- Fixed entry (z > 2.0) and exit (z < 0.5) thresholds
- Basic transaction cost modeling (5 bps)
- Performance metrics: Sharpe, drawdown, VaR/CVaR
- Yearly excess returns vs SPY
- Correlation matrices

**This is the "clean" version** - straightforward statistical arbitrage without ML.

---

#### 2. `Volatility_Dispersion_ML_Enhanced.ipynb`
**Role:** EXPERIMENTAL ENHANCEMENT

This notebook **builds on the baseline** by adding:
- **Machine Learning Filter:** Random Forest classifier
- **40+ Engineered Features:**
  - Spread momentum (5d, 10d, 20d)
  - Volatility ratios and trends
  - Correlation stability metrics
  - Mean-reversion quality indicators
  - VIX regime indicators
- **Walk-Forward Validation:** Quarterly retraining (63-day frequency)
- **Adaptive Thresholds:** Entry adjusted by VIX level
- **Side-by-Side Comparison:** ML vs non-ML performance

**Key Addition:** `backtest_vol_dispersion_ml()` function with ML integration

---

#### 3. `Improved_Basket_Pair_Trading_Strategy.ipynb`
**Role:** COMPREHENSIVE / FINAL VERSION

This is the **most complete notebook** combining everything:
- All baseline functionality
- All ML enhancements
- **Additional Analysis:**
  - ADF stationarity testing at each time step
  - Half-life calculation (Ornstein-Uhlenbeck estimation)
  - Quality filters (only trade when spread is stationary)
  - Dynamic position sizing based on half-life
  - Detailed performance attribution by regime
  - Basic vs Enhanced strategy comparison charts

**This appears to be the "final deliverable"** for the course project.

---

## Are There Duplicates?

### Yes and No

**Overlap exists because each notebook represents an iteration:**

| Component | Baseline | ML-Enhanced | Improved |
|-----------|----------|-------------|----------|
| Basket definitions | Yes | Yes | Yes |
| `basket_index()` function | Yes | Yes | Yes |
| Basic backtest function | Yes | Yes | Yes |
| ML feature engineering | No | Yes | Yes |
| ML training/prediction | No | Yes | Yes |
| Stationarity testing | No | No | Yes |
| Half-life analysis | No | No | Yes |
| Performance attribution | No | No | Yes |

**The notebooks are NOT testing different things** - they're testing the **same strategy with progressive enhancements**.

---

## Recommended Organization

### Current State: Messy but Functional

The repo has **evolutionary code** where each notebook builds on the previous. This is typical for research projects but creates redundancy.

### If Cleaning Up:

**Option A: Keep All Three** (Current)
- Useful for showing progression of ideas
- Good for academic submission showing iterative improvement

**Option B: Consolidate to Two**
- Keep `Volatility Dispersion - Statistical Basket Pairs Trading Strategy.ipynb` as baseline reference
- Keep `Improved_Basket_Pair_Trading_Strategy.ipynb` as the final version
- Archive `Volatility_Dispersion_ML_Enhanced.ipynb` (it's a stepping stone)

**Option C: Single Notebook**
- Merge everything into one comprehensive notebook
- Use sections/flags to toggle ML on/off
- Cleanest but loses development history

---

## PDF Reports

| Report | Contents |
|--------|----------|
| `Exec Comparison Summary.pdf` | Side-by-side performance metrics, likely generated from baseline notebook |
| `ML Enhanced Strategy Comparison.pdf` | Detailed ML analysis, feature importance, comparison charts |

These appear to be **exported/generated reports** from the notebooks, not standalone documents.

---

## Summary

| Question | Answer |
|----------|--------|
| Are there old vs new files? | Yes - three notebooks represent evolution |
| Are they testing the same thing? | Yes - same strategy, progressive enhancements |
| Is there duplicate code? | Yes - each notebook copies previous + adds more |
| Which is the "final" version? | `Improved_Basket_Pair_Trading_Strategy.ipynb` |
| Which is the cleanest baseline? | `Volatility Dispersion - Statistical Basket Pairs Trading Strategy.ipynb` |

---

## Tech Stack

- **Language:** Python 3
- **Data:** Yahoo Finance (yfinance)
- **Analysis:** pandas, numpy, scipy, statsmodels
- **ML:** scikit-learn (RandomForestClassifier)
- **Visualization:** matplotlib, seaborn
- **Environment:** Jupyter Notebooks
