# Overview of Consolidating Candles

This Pine Script identifies consolidation periods by detecting when a specified percentage of recent candles' price action remains within a narrow range. It visually marks these periods with a colored box on the chart and optionally displays a summary table with relevant statistics.

## Key Features & Functionality
- Defining Pip Size
 
    The script determines the pip size dynamically based on the symbol.

    If the instrument is a JPY pair, the pip size is set to 0.20, otherwise, it's 0.0015.

- Input Parameters
  
  - Box colors for different consolidation conditions.

  - Percentage threshold (default: 90%) to determine whether price action is consolidating.

  - Lookback periods for different timeframes (30 min, 1hr, 2hr, 4hr).

## Dynamic Lookback Periods
The script adjusts the lookback window based on the chart’s timeframe:

30-minute chart → 32 candles

1-hour chart → 24 candles

2-hour chart → 12 candles

4-hour chart → 9 candles

## Identifying Consolidation Zones
The script calculates a midpoint price range from the previous candle’s high/low, including wicks.

It determines the top and bottom bounds of the consolidation range based on pip size.

It checks how many of the past lookback candles stayed within this range.

## Drawing the Consolidation Box
If the percentage of candles within the box meets or exceeds the threshold, the script colors the box red (default). Otherwise, it colors the box green.

The box is drawn dynamically, updating as new candles form.

# Overview of EMA Functionality
The Exponential Moving Average (EMA) functionality in the combined script serves as a core feature for determining the trend direction based on the moving average of the price. Here’s a breakdown of how it works:

## EMA Calculation:
The script calculates the Exponential Moving Average (EMA) using the ta.ema(close, length) function.

Input Parameter: length is the period of the EMA (default is 9).

This EMA is computed based on the closing prices of the specified period.

Comparison with Past EMA:

The script also calculates the EMA value from 24 hours ago (24 bars ago in the chart’s timeframe), using ema_now[24].

This allows comparison between the current EMA and the EMA from the past to determine if the trend is upward, downward, or sideways.

## Determining Trend Direction:
Uptrend: If the current EMA (ema_now) is greater than the EMA from 24 hours ago (ema_past), the trend is considered up.

Indicator: An upward arrow (🔼) is displayed.

Background Color: The background is green if the trend is strong (i.e., the EMA change is above the threshold), or orange if the trend is weak (i.e., the EMA change is below the threshold).

Downtrend: If the current EMA is less than the past EMA, the trend is considered down.

Indicator: A downward arrow (🔽) is displayed.

Background Color: Similar to an uptrend, the background color changes based on the strength of the trend.

Sideways (No significant trend): If the current EMA is close to the past EMA (i.e., little change), it indicates a sideways market.

Indicator: A sideways arrow (➖) is displayed.

Background Color: The background will be amber (default for weak trends).

## Trend Strength (Background Color):
The strength of the trend is determined by the percentage change between the current EMA and the EMA from 24 hours ago.

Formula:

\[
\text{EMA Change} = \left( \frac{| \text{EMA Now} - \text{EMA Past} |}{\text{EMA Past}} \right) \times 100
\]

If the change exceeds the threshold (default 0.5%), it indicates a strong trend and the background color is set to green.

If the change is below the threshold, the background is set to amber, indicating a weak or insignificant trend.

## Debug Mode (EMA):
Debug Mode can be toggled on (debug_ema = true), which will display additional information about the EMA on the chart.

Current EMA Value: This is displayed above the current candle (or bar) in green for uptrends, red for downtrends, and gray for sideways movement.

EMA Value from 24 Hours Ago: Displayed below the current candle, with colors inversely matching the trend direction (e.g., red if the trend is up, green if the trend is down).

Purpose: This mode helps in visualizing the EMA values and understanding how the trend is developing over time.

## Table Display (EMA Information):
A table is displayed in the top-right corner of the chart that shows the direction of the trend (using the up, down, or sideways arrows) and the trend strength based on the EMA change.

The table updates in real-time as the trend shifts and the EMA is recalculated.

Trend direction is represented by an arrow, and the background color of the table adjusts based on whether the trend is strong (green) or weak (amber).



# How to install 

## Step 1: Open the Pine Script Editor

- Log in to your TradingView account.
- Open a chart by clicking on "Chart" from the main menu.
- In the bottom panel of the chart window, click on "Pine Editor" to open the script editor.

## Step 2: Create a New Script

- In the Pine Script Editor, you will see either a blank editor or a default script.
- Delete any existing text to start fresh.
- Open the file named ConsolidatingCandles.pine.
- Copy the script text from the file.
- Paste the copied text into the Pine Script Editor.
- Click "Save", then enter a name for your script.

## Step 3: Add the Indicator to the Chart

- Click on the "Add to Chart" button at the top of the Pine Script Editor.
- If the script is error-free, the indicator will be applied to the chart.

  
