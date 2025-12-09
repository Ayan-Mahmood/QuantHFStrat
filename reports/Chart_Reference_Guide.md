# Chart Reference Guide for v5 Notebook

## Quick Reference: Which Chart is Which

Use this guide to match the PowerPoint slide placeholders to the charts in the v5 notebook.

---

## Chart Mapping (with Line Numbers)

| Slide # | Slide Title | Notebook Line # | Code Section Header |
|---------|-------------|-----------------|---------------------|
| **7** | Feature Importance | ~1943 | `# ML FEATURE IMPORTANCE ANALYSIS` |
| **9** | Cumulative Returns | ~2071 | `# CUMULATIVE RETURNS - 2x2 GRID` |
| **10** | Drawdown Profile | ~2233 | `# DRAWDOWN VISUALIZATION - CLEAN STYLING` |
| **12** | Rolling Sharpe | ~1766 | `# ROLLING SHARPE RATIO (252-DAY WINDOW)` |
| **13** | Alpha Analysis | ~1702 | `# CUMULATIVE ALPHA (EXCESS RETURN) CHART` |
| **14** | Monthly Heatmap | ~1835 | `# MONTHLY RETURNS HEATMAP` |
| **16** | Correlation Matrix | ~2006 | `# STRATEGY CORRELATION MATRIX` |

### Order in Notebook (top to bottom):
1. Line 1702 - Cumulative Alpha (Slide 13)
2. Line 1766 - Rolling Sharpe (Slide 12)
3. Line 1835 - Monthly Heatmap (Slide 14)
4. Line 1943 - Feature Importance (Slide 7)
5. Line 2006 - Correlation Matrix (Slide 16)
6. Line 2071 - Cumulative Returns 2x2 (Slide 9)
7. Line 2233 - Drawdown 2x2 (Slide 10)

---

## How to Export Charts

After running each cell, right-click on the chart and "Save Image As" or add this code after each figure:

```python
plt.savefig('chart_name.png', dpi=150, bbox_inches='tight', facecolor='white')
```

---

## Code Section Comments to Add

Add these comments BEFORE each chart cell to make them easy to find:

### Cell: Feature Importance (Slide 7)
```python
# =============================================================================
# CHART FOR SLIDE 7: FEATURE IMPORTANCE
# Export as: feature_importance.png
# =============================================================================
```

### Cell: Cumulative Returns (Slide 9)
```python
# =============================================================================
# CHART FOR SLIDE 9: CUMULATIVE RETURNS (ML STRATEGY)
# Export as: cumulative_returns.png
# =============================================================================
```

### Cell: Drawdown (Slide 10)
```python
# =============================================================================
# CHART FOR SLIDE 10: DRAWDOWN PROFILE
# Export as: drawdown_chart.png
# =============================================================================
```

### Cell: Rolling Sharpe (Slide 12)
```python
# =============================================================================
# CHART FOR SLIDE 12: ROLLING SHARPE RATIO
# Export as: rolling_sharpe.png
# =============================================================================
```

### Cell: Cumulative Alpha (Slide 13)
```python
# =============================================================================
# CHART FOR SLIDE 13: CUMULATIVE ALPHA VS SPY
# Export as: cumulative_alpha.png
# =============================================================================
```

### Cell: Monthly Heatmap (Slide 14)
```python
# =============================================================================
# CHART FOR SLIDE 14: MONTHLY RETURNS HEATMAP
# Export as: monthly_heatmap.png
# =============================================================================
```

### Cell: Correlation Matrix (Slide 16)
```python
# =============================================================================
# CHART FOR SLIDE 16: STRATEGY CORRELATION MATRIX
# Export as: correlation_matrix.png
# =============================================================================
```

---

## IMPORTANT: ML vs Baseline vs SPY Comparison

### Current Issue
The current charts only show:
- Baseline Strategy vs SPY, OR
- ML Strategy alone

### What Should Be Shown
For a complete comparison, show ALL THREE:
1. **ML Strategy** (our improved version)
2. **Baseline Strategy** (no ML filter)
3. **SPY** (benchmark)

### Why This Matters
- Professor Sharma will ask: "Why not just buy SPY?"
- You need to show ML beats Baseline AND how both compare to SPY
- The ML version is your "final product" - lead with that

### Recommended Chart Update
For the **Cumulative Returns** chart (Slide 9), update to show:
```
Line 1: ML Strategy (Stevens Red, solid, thick)
Line 2: Baseline Strategy (Gray, dashed)
Line 3: SPY Benchmark (Black, thin)
```

This tells the story:
- "Here's what SPY did"
- "Here's what our baseline did"
- "Here's how ML improved it"

---

## Chart Style Checklist

Before exporting each chart, verify:

- [ ] Title is BLACK (not colored)
- [ ] Axis labels are BOLD
- [ ] No unnecessary gridlines
- [ ] Lines are SOLID (not dotted) unless intentionally dashed for comparison
- [ ] Stevens Red (#9D1535) used for primary strategy line
- [ ] Legend is clear and positioned well
- [ ] White background
