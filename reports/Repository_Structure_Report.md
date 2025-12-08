# Repository Structure Report: QuantHFStrat

## Overview

This repository contains research for **FE571: Quantitative Hedge Fund Trading Strategies** (Group 7 Final Project). The project implements volatility dispersion trading strategies with progressive enhancements.

---

## Folder Structure

```
QuantHFStrat/
├── backtesting/
│   ├── v1_Volatility_Dispersion_Baseline.ipynb
│   ├── v2_Volatility_Dispersion_ML_Enhanced.ipynb
│   └── v3_Improved_Basket_Pair_Trading_Strategy.ipynb
├── pdfs/
│   ├── Exec_Comparison_Summary.pdf
│   └── ML_Enhanced_Strategy_Comparison.pdf
├── reports/
│   ├── Executive_Report_v1.md
│   └── Repository_Structure_Report.md
├── .gitignore
├── LICENSE
└── README.md
```

---

## File Inventory

### Backtesting Notebooks

| File | Lines | Size | Purpose |
|------|-------|------|---------|
| `backtesting/v1_Volatility_Dispersion_Baseline.ipynb` | 782 | 991 KB | **BASELINE** - Original implementation |
| `backtesting/v2_Volatility_Dispersion_ML_Enhanced.ipynb` | 666 | 1.0 MB | **ENHANCED** - Adds ML layer to baseline |
| `backtesting/v3_Improved_Basket_Pair_Trading_Strategy.ipynb` | 1,954 | 684 KB | **COMPREHENSIVE** - Most complete version |

### PDF Reports

| File | Size | Purpose |
|------|------|---------|
| `pdfs/Exec_Comparison_Summary.pdf` | 1.8 MB | Performance comparison report |
| `pdfs/ML_Enhanced_Strategy_Comparison.pdf` | 2.9 MB | ML enhancement analysis |

### Documentation

| File | Purpose |
|------|---------|
| `reports/Executive_Report_v1.md` | Executive summary of strategy performance |
| `reports/Repository_Structure_Report.md` | This file - repo organization guide |
| `README.md` | Project description |
| `LICENSE` | MIT License (Ayan Mahmood) |

---

## Code Evolution & Relationships

### The Three Notebooks Explained

```
PROGRESSION:

  [v1] BASELINE              [v2] ML-ENHANCED             [v3] COMPREHENSIVE
  (Original Strategy)   -->  (Adds ML Filter)    -->     (Full Analysis)

  - Basic vol spread          - Random Forest              - Everything from v1 & v2
  - Fixed thresholds          - 40+ features               - Stationarity testing
  - Simple backtest           - Walk-forward validation    - Half-life analysis
  - Performance metrics       - VIX regime adaptation      - Performance attribution
                              - Sharpe comparison          - Yearly excess returns
                                                           - Correlation analysis
```

### Detailed Breakdown

#### v1: `backtesting/v1_Volatility_Dispersion_Baseline.ipynb`
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

#### v2: `backtesting/v2_Volatility_Dispersion_ML_Enhanced.ipynb`
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

#### v3: `backtesting/v3_Improved_Basket_Pair_Trading_Strategy.ipynb`
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

**This is the final deliverable** for the course project.

---

## Are There Duplicates?

### Yes and No

**Overlap exists because each notebook represents an iteration:**

| Component | v1 Baseline | v2 ML-Enhanced | v3 Improved |
|-----------|-------------|----------------|-------------|
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

## PDF Reports

| Report | Contents |
|--------|----------|
| `pdfs/Exec_Comparison_Summary.pdf` | Side-by-side performance metrics from baseline notebook |
| `pdfs/ML_Enhanced_Strategy_Comparison.pdf` | Detailed ML analysis, feature importance, comparison charts |

These are **exported/generated reports** from the notebooks.

---

## Summary

| Question | Answer |
|----------|--------|
| Are there old vs new files? | Yes - three notebooks represent evolution (v1 → v2 → v3) |
| Are they testing the same thing? | Yes - same strategy, progressive enhancements |
| Is there duplicate code? | Yes - each notebook copies previous + adds more |
| Which is the "final" version? | `v3_Improved_Basket_Pair_Trading_Strategy.ipynb` |
| Which is the cleanest baseline? | `v1_Volatility_Dispersion_Baseline.ipynb` |

---

## Tech Stack

- **Language:** Python 3
- **Data:** Yahoo Finance (yfinance)
- **Analysis:** pandas, numpy, scipy, statsmodels
- **ML:** scikit-learn (RandomForestClassifier)
- **Visualization:** matplotlib, seaborn
- **Environment:** Jupyter Notebooks
