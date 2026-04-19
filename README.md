# IPCA forecast — aggregated vs. disaggregated

ARIMA-based inflation forecasting for Brazil's IPCA index, comparing aggregated and disaggregated approaches across 9 consumption groups, benchmarked against the BCB Focus market expectations report.

## Research question

*Does forecasting IPCA by disaggregated consumption groups and aggregating the results produce more accurate projections than forecasting the total index directly?*

## Approach

1. **Data** — monthly IPCA series from BCB API (total + 9 groups)
2. **Aggregated model** — single ARIMA fitted to IPCA total, minimizing RMSE on test set
3. **Disaggregated model** — individual ARIMA per group (food, housing, health, transport, etc.), forecasts aggregated by weight
4. **Model selection** — grid search over ARIMA(p,d,q) by AIC on training sample
5. **Benchmark** — comparison against BCB Focus median expectations

## Groups modeled

Food and beverages · Housing · Household goods · Clothing · Transportation · Health · Personal expenses · Education · Communication

## Key results

- Disaggregated approach captures group-specific dynamics not visible in the aggregate
- Model selection based on RMSE on held-out test period
- Final projection compared against Focus report reference date

## Data

- Source: BCB API (Banco Central do Brasil)
- Frequency: monthly
- Series: IPCA total + 9 consumption groups

## Stack

R · forecast · rbcb · ggplot2 · tidyverse

## Structure

```
├── Forum1_TS_AlexisMeneses.ipynb    ← main notebook
└── README.md
```

## How to run

```r
install.packages(c("forecast", "rbcb", "ggplot2", "tidyverse"))
```

Data is loaded automatically via BCB API — no local file needed.

## Structure
