# Area Chart Overlay Indicator - Technical Specification

## Project Goal
Create a Pine Script v5 indicator that visually clones the TradingView "Area" chart style while functioning as an overlay on top of candlestick charts.

## Core Requirements

### 1. Overlay Configuration
- **Requirement:** Must use `overlay=true` in the indicator declaration
- **Rationale:** Ensures the indicator stays pinned to the main price pane and maintains a 1:1 price scale relationship
- **Implementation:** Set `indicator("Name", overlay=true)`

### 2. Price Source Tracking
- **Requirement:** The top edge of the area must track the `close` price exactly
- **Rationale:** Maintains visual consistency with the native Area chart behavior
- **Implementation:** Use `close` (or user-selectable source) as the top plot value

### 3. Visual Layering
- **Requirement:** The gradient fill must sit **on top** of the candlesticks (not behind them)
- **Rationale:** Creates a "glass overlay" effect where candlesticks remain visible through the colored gradient
- **Implementation:** Do NOT use `behind_chart=true`; rely on default indicator layering behavior

### 4. Gradient Fill Implementation
- **Requirement:** Implement a vertical gradient that fades from a user-defined solid color at the price line to 100% transparency at the bottom
- **Rationale:** Replicates the Area chart's smooth color transition effect
- **Implementation:** Use `fill()` function with `top_color` (semi-transparent) and `bottom_color` (fully transparent)

### 5. Dynamic Baseline
- **Requirement:** The baseline for the gradient must be dynamic or offset so it doesn't "squash" the candle height or force the price scale to zoom out to zero
- **Rationale:** A fixed zero baseline would compress candlesticks and make them unreadable
- **Implementation:** Calculate baseline as a percentage offset below the current price (e.g., 10% below close)

## Technical Specifications

### User Inputs
- **Price Source:** Selectable price source (default: `close`)
- **Area Color:** Primary color for the gradient (with transparency control)
- **Fade/Bottom Color:** Bottom color (should be fully transparent)
- **Top Line Color:** Color for the price line (optional, can be transparent)
- **Gradient Depth:** Percentage value controlling how far the gradient extends downward (default: 10%)

### Visual Behavior
- **Top Line:** Solid line at the selected price source
- **Gradient Fill:** Smooth vertical transition from semi-transparent color to fully transparent
- **Layering:** Indicator renders above candlesticks, creating glass overlay effect
- **Scale Preservation:** Baseline offset prevents price scale distortion

### Edge Cases to Handle
- Ensure gradient depth doesn't exceed reasonable bounds (e.g., 1-50%)
- Handle cases where price source might be zero or negative
- Maintain performance with large datasets

## Success Criteria
1. ✅ Indicator overlays on candlestick charts without disrupting price scale
2. ✅ Gradient visually matches Area chart aesthetic
3. ✅ Candlesticks remain clearly visible through the overlay
4. ✅ Top line tracks price source accurately
5. ✅ User can customize colors and gradient depth
6. ✅ No performance degradation on standard chart timeframes

## Optional Enhancements
- Dynamic color based on price direction (green for rising, red for falling)
- Multiple gradient depth presets
- Animation effects
- Volume-weighted area coloring

