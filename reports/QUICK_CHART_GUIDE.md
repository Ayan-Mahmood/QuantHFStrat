# QUICK CHART GUIDE - Copy to v5 Notebook

## Add These Comments Before Each Chart Cell

### Chart 1: Cumulative Alpha vs SPY (Line ~1699) → SLIDE 13
```python
# =============================================================================
# SLIDE 13: CUMULATIVE ALPHA (EXCESS RETURN VS SPY)
# Export as: cumulative_alpha.png
# =============================================================================
```

### Chart 2: Rolling Sharpe Ratio (Line ~1763) → SLIDE 12
```python
# =============================================================================
# SLIDE 12: ROLLING SHARPE RATIO (252-DAY)
# Export as: rolling_sharpe.png
# =============================================================================
```

### Chart 3: Monthly Returns Heatmap (Line ~1818) → SLIDE 14
```python
# =============================================================================
# SLIDE 14: MONTHLY RETURNS HEATMAP
# Export as: monthly_heatmap.png
# =============================================================================
```

### Chart 4: Feature Importance (Line ~1913) → SLIDE 7
```python
# =============================================================================
# SLIDE 7: ML FEATURE IMPORTANCE (RANDOM FOREST)
# Export as: feature_importance.png
# =============================================================================
```

### Chart 5: Strategy Correlation Matrix (Line ~2000) → SLIDE 16
```python
# =============================================================================
# SLIDE 16: STRATEGY CORRELATION MATRIX
# Export as: correlation_matrix.png
# =============================================================================
```

### Chart 6: Cumulative Returns 2x2 Grid (Line ~2067) → SLIDE 9
```python
# =============================================================================
# SLIDE 9: CUMULATIVE RETURNS (ML vs BASELINE per pair)
# Export as: cumulative_returns.png
# Shows: 4 pairs, each with ML (red) and Baseline (gray) lines
# =============================================================================
```

### Chart 7: Drawdown 2x2 Grid (Line ~2230) → SLIDE 10
```python
# =============================================================================
# SLIDE 10: DRAWDOWN PROFILE
# Export as: drawdown_chart.png
# =============================================================================
```

---

## IMPORTANT: About ML vs Baseline vs SPY

The current 2x2 Cumulative Returns chart (Slide 9) shows:
- **ML Strategy** (Stevens Red line)
- **Baseline Strategy** (Gray line)

This is correct! It shows how ML improves on baseline.

For SPY comparison, use the **Cumulative Alpha chart** (Slide 13) which shows excess return vs SPY.

### The Full Story for Professor Sharma:
1. **Slide 9 (Cumulative Returns)**: Shows ML beats Baseline
2. **Slide 13 (Cumulative Alpha)**: Shows both strategies vs SPY benchmark

This tells the complete narrative:
- "Here's our baseline strategy"
- "Here's how ML improved it"
- "Here's how both compare to just buying SPY"
