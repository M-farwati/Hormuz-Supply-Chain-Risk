# Strategic-Risk-Assessment---Strait-of-Hormuz
Quantifying Geopolitical Disruptions in Japan’s Maritime Supply Chain - My 1st Data Analytics Project

📂 Project Overview: This repository contains the data and methodology used to model the financial impact of maritime throughput volatility in the Strait of Hormuz. By bridging the gap between UNCTAD Macro-Economic Trade Values and IMF PortWatch Daily Vessel Traffic, this study identifies a specific 20.7% disruption event and calculates the resulting "Value at Risk" for the Japanese economy.

🛠️ Technical Stack: 
* Data Sourcing: UNCTAD (Merchandise Trade), IMF PortWatch (Maritime Transit)
* Analysis: SQL (Data Filtering & Aggregation), Excel (Time-Series Delta Modeling)
  

🚀 The Data Workflow: 
1. Data Extraction & Cleaning (SQL)To establish the baseline, I queried the UNCTAD dataset to isolate Japan's trade trajectory. I encountered a "String-to-Date" mismatch in the IMF timestamps, which required a LIKE operator or SUBSTRING logic to align the daily traffic with the 2022 calendar year.
SQL/

* Extracting Japan's 2022 Import Baseline */
SELECT 
    Year, 
    `US_at_current_prices_in_millions` AS Import_Value
FROM `unctad_data`
WHERE Economy_label = 'Japan' 
  AND Year = 2022 
  AND `Flow Label` = 'Import';

2. Quantitative Modeling (Excel/SQL)
I performed a 7-Day Moving Average Delta Analysis. By comparing the current volume to the prior year's baseline, I identified a significant volatility spike.

Key Calculation: 
* Daily Import Baseline (Japan): $897M /365 =$2.45M$
* Hormuz Exposure (20% weight): $491k
* Calculated Value at Risk (VaR): $491k times 20.7% = $101k

📈 Key Visuals: 
* The Value at Risk Waterfall. This chart illustrates the "funneling" of macro-trade data into a daily operational risk metric.
* The 2022 Volatility Map: A time-series visualization highlighting the November 27th dip of -20.7% in vessel transit volume.

💡 Strategic Insights 
* The Energy Tax: Japan’s import costs are rising 2x faster than exports, largely driven by energy price volatility in maritime chokepoints.
* The Buffer Gap: A 20.7% volume drop suggests that "Just-in-Time" inventories are insufficient; a 21-day safety stock expansion is recommended for Tier-1 suppliers.
