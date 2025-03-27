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

  
