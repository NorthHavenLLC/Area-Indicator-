Area Chart Overlay Clone (Pine Script v5)
📌 Project Overview

The Area Chart Overlay Clone is a specialized TradingView indicator designed to bring the visual aesthetic of the native "Area" chart style directly onto a candlestick chart.

While TradingView typically requires you to choose either candles or an area chart, this script allows for both. It creates a 1:1 price-pinned gradient that sits on top of your candlesticks, providing a modern, "glass-layered" look while maintaining full technical visibility.
✨ Key Features

    1:1 Price Mapping: The top boundary of the gradient is hard-coded to the close price, ensuring perfect alignment with your candles.

    "Over-Top" Layering: Unlike standard background fills, this indicator is rendered in the foreground, creating a sleek overlay effect.

    Dynamic Baseline Logic: To prevent the price scale from "squashing" (a common issue when area charts try to fill to zero), this script uses a floating baseline that follows the price at a user-defined percentage.

    Fully Customizable: Easily adjust colors, line thickness, and transparency through the settings menu.

🚀 Installation

    Open TradingView: Navigate to your desired chart.

    Open Pine Editor: Click the "Pine Editor" tab at the bottom of the screen.

    Paste Code: Clear any existing text and paste the provided script.

    Save: Click the "Save" button and name the script (e.g., Area Overlay Clone).

    Add to Chart: Click the "Add to Chart" button.

🛠 Settings & Inputs
Input	Type	Description
Price Source	Source	Defines which price data the line tracks (Default: Close).
Area Color	Color	The color at the very top of the gradient (includes transparency).
Fade Color	Color	The color at the bottom of the gradient (usually set to 100% transparent).
Gradient Depth %	Float	Controls how far down the "paint" drips relative to the current price.
💡 Technical Implementation Details

This script solves the Scale Integrity problem. In a standard Area chart, the fill goes to $0.00. On an overlay, this would make your candlesticks appear as tiny dots at the top of the screen.

The Solution: The script calculates a hidden baseline using the following formula:
Baseline=Price×(1−100Depth %​)

This keeps the gradient "pinned" to the price action without forcing the Y-axis to zoom out to zero.
⚖️ Disclaimer

This indicator is for visual and aesthetic purposes only. It does not provide buy/sell signals. Trading involves significant risk, and you should use this tool as a supplement to your existing strategy.
<img width="456" height="359" alt="Screenshot 2026-01-07 at 8 11 54 PM" src="https://github.com/user-attachments/assets/8da2b3c9-6087-40e5-ab14-85ff9d559917" />
