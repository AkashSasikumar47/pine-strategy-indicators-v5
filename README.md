# Pine Strategy Indicators v5

## Overview

A collection of five Pine Script technical indicators for TradingView, designed for trend analysis, momentum measurement, and dynamic stop-loss management. These indicators utilize volatility-based calculations, adaptive algorithms, and momentum oscillators to provide actionable trading signals.

## Included Indicators

### Supertrend Indicator

**Purpose:** Identifies market trends and potential reversal points using volatility-based bands.

**Core Logic:** Calculates upper and lower bands using ATR (Average True Range) multiplied by a configurable factor. Supports three simultaneous Supertrend lines with independent parameters. Trend direction changes when price crosses the bands, generating buy/sell signals with visual markers.

**Key Parameters:**

- ATR Period: 10, 11, 12 (for Lines 1, 2, 3)
- ATR Multiplier: 1.0, 2.0, 3.0 (for Lines 1, 2, 3)
- Line Toggles: Enable/disable individual lines

![Supertrend Indicator](images/Supertrend-Indicator.png)

**Typical Use Case:** Follow trends by buying when price is above the Supertrend line (uptrend) and selling when price falls below it (downtrend). Multiple lines provide confirmation and varying sensitivity levels.

---

### Adaptive Moving Average

**Purpose:** Provides a dynamic moving average that adjusts smoothing based on market efficiency.

**Core Logic:** Implements Kaufman's Adaptive Moving Average (KAMA) algorithm. Calculates an efficiency ratio by comparing net price change to total volatility over a period. Adjusts the smoothing constant between fast and slow EMA alphas based on this efficiency, resulting in faster response during trending markets and slower response during choppy conditions.

**Key Parameters:**

- Length: 14 (lookback period for efficiency calculation)
- Fast EMA Length: 2 (responsive smoothing constant)
- Slow EMA Length: 30 (conservative smoothing constant)
- Highlight Movements: Color-coded trend direction

![Adaptive Moving Average](images/Adaptive-Moving-Average.png)

**Typical Use Case:** Use as a dynamic trend filter that reduces whipsaws in sideways markets while remaining responsive to genuine trends. Price above AMA suggests uptrend; price below suggests downtrend.

---

### Relative Momentum Index

**Purpose:** Measures momentum strength by analyzing price changes over multiple periods rather than single-period shifts.

**Core Logic:** Similar to RSI but replaces single-period price changes with N-period momentum changes. Calculates the ratio of average upward momentum to average downward momentum over a specified length, then normalizes to a 0-100 scale. Uses RMA (Running Moving Average) for smoothing.

**Key Parameters:**

- Length: 14 (RSI-style smoothing period)
- Momentum Length: 3 (multi-period change calculation)
- Highlight Breakouts: Visual emphasis for overbought/oversold zones
- Overbought Level: 70
- Oversold Level: 30

![Relative Momentum Index](images/Relative-Momentum-Index.png)

**Typical Use Case:** Identify overbought conditions (RMI > 70) suggesting potential reversals or profit-taking, and oversold conditions (RMI < 30) suggesting potential buying opportunities. Provides smoother signals than traditional RSI.

---

### Chandelier Exit

**Purpose:** Dynamic trailing stop-loss that adjusts based on ATR to protect positions while allowing room for volatility.

**Core Logic:** Sets long stops at the highest high (or highest close) minus ATR multiplied by a factor, and short stops at the lowest low (or lowest close) plus ATR multiplied by a factor. Stops only move in the direction of the trend, never against it. Direction flips when price crosses the opposite stop level.

**Key Parameters:**

- ATR Period: 22 (volatility measurement length)
- ATR Multiplier: 3.0 (stop distance from extremes)
- Use Close Price for Extremums: True/False
- Show Buy/Sell Labels: Visual signal markers
- Highlight State: Color-coded trend zones

![Chandelier Exit](images/Chandelier-Exit.png)

**Typical Use Case:** Use as a trailing stop-loss mechanism that widens during high volatility and tightens during low volatility. Automatically adjusts to market conditions, reducing the risk of premature stop-outs.

---

### Trend Strength Index

**Purpose:** Quantifies the strength of a trend by comparing net price change to cumulative volatility.

**Core Logic:** Calculates total volatility as the sum of absolute period-to-period price changes over N periods. Measures net price change from the current close to N periods ago. The TSI is the ratio of net change to total volatility, smoothed with a simple moving average. Higher values indicate strong directional movement relative to noise.

**Key Parameters:**

- Length: 30 (volatility and change calculation period)
- Smoothing: 5 (SMA smoothing for primary TSI line)
- Additional smoothing line: 100-period SMA for trend context

![Trend Strength Index](images/Trend-Strength-Index.png)

**Typical Use Case:** Assess whether a trend has conviction. Rising TSI confirms strong trends; declining TSI signals weakening momentum or potential consolidation. Compare short-term (5-period) and long-term (100-period) smoothing for trend context.

---

## How to Use

1. Open TradingView and navigate to the Pine Editor
2. Copy the desired indicator's Pine Script code from the `indicators/` folder
3. Paste the code into the Pine Editor
4. Click "Add to Chart" to apply the indicator
5. Adjust parameters through the indicator settings menu as needed
6. Save the indicator to your TradingView library for future use

All indicators are compatible with Pine Script versions 3 and 4. They can be applied to any timeframe and asset class supported by TradingView.

---

## Disclaimer

These indicators are provided for educational and informational purposes only. They do not constitute financial advice or trading recommendations. Past performance of any trading strategy or indicator does not guarantee future results. Users are responsible for their own trading decisions and risk management.
