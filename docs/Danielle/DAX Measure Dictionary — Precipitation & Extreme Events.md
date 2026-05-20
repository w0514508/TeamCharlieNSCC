# 📘 DAX Measure Dictionary — Precipitation, Temperature & Extreme Events

This document describes all DAX measures used in the Power BI model.  
Measures are documented with a focus on **analytical intent**, **data grain**, and **appropriate usage**, rather than DAX syntax.

---

## 🌧️ Precipitation Measures

### `Monthly Precipitation (mm)`
- **Description:** Total precipitation aggregated across all stations.
- **Grain:** Monthly (Year / Month).
- **Purpose:** Base measure for precipitation analysis, including averages, anomalies, and wet‑month indicators.

---

### `Avg Monthly Precipitation (mm)`
- **Description:** Average monthly precipitation across all locations.
- **Grain:** Monthly.
- **Purpose:** Describes typical monthly precipitation behavior.
- **Notes:** Serves as a building block for annual averages and anomaly calculations.

---

### `Long-Term Avg Monthly Precipitation (mm)`
- **Description:** Long-term historical average precipitation for each calendar month.
- **Grain:** Monthly, aggregated across all years (1995–2025).
- **Purpose:** Baseline used to classify months as below, normal, or above average.

---

### `Monthly Precipitation Anomaly (mm)`
- **Description:** Difference between observed monthly precipitation and the long-term monthly average.
- **Grain:** Monthly.
- **Interpretation:** Positive values indicate wetter-than-normal months; negative values indicate drier-than-normal months.
- **Purpose:** Analyzes changes in precipitation behavior relative to historical norms.

---

### `Avg Annual Precipitation (mm)`
- **Description:** Average of annual total precipitation across all available years.
- **Grain:** Annual (derived from monthly data).
- **Purpose:** Provides high-level climate context.
- **Limitations:** Not used to analyze extremes or variability.

---

### `Avg Precip per Station`
- **Description:** Average precipitation calculated per station, then averaged across all stations.
- **Grain:** Station-level aggregated to monthly or annual context.
- **Purpose:** Ensures equal contribution of each station in the analysis.
- **Notes:** Avoids bias caused by uneven station distribution.

---

### `Total Precip per Year`
- **Description:** Total precipitation aggregated at the yearly level.
- **Grain:** Annual.
- **Purpose:** Supports cross-year comparisons and trend evaluation.
- **Notes:** Overrides lower-level filters to preserve full yearly context.

---

### `Precip Index (Per Station)`
- **Description:** Indexed precipitation measure using 1995 as the base year (index = 100).
- **Grain:** Monthly or annual.
- **Purpose:** Enables comparison of relative changes in precipitation over time.
- **Interpretation:** Values above 100 indicate increases relative to the base year.

---

---

## 🌧️ Precipitation — Trend & Variability

### `YoY Precip Change`
- **Description:** Year-over-year percentage change in total precipitation.
- **Grain:** Annual.
- **Purpose:** Captures short-term fluctuations in precipitation patterns.

---

### `YoY Precip Change (Adj)`
- **Description:** Year-over-year change in average precipitation per station using explicit year context.
- **Grain:** Annual.
- **Purpose:** Provides a more controlled and stable comparison than standard time intelligence functions.
- **Notes:** Less sensitive to visual-level filtering.

---

### `Precip Trend %`
- **Description:** Long-term percentage change in precipitation over a 10-year period.
- **Grain:** Annual.
- **Purpose:** Identifies structural trends rather than short-term variability.

---

### `Monthly Precipitation Variability`
- **Description:** Relative variability of precipitation measured using the coefficient of variation.
- **Grain:** Monthly.
- **Purpose:** Quantifies how unstable or unpredictable precipitation levels are over time.
- **Interpretation:** Higher values indicate greater variability and uncertainty.

---

---

## 🌧️ Precipitation — Frequency Indicators

### `Wet Month Flag (Regional)`
- **Description:** Flags whether a calendar month qualifies as a wet month.
- **Logic:** Monthly precipitation exceeds the long-term monthly baseline.
- **Output:** 1 = wet month, 0 = not wet.
- **Purpose:** Building block for frequency-based precipitation indicators.

---

### `Wet Months per Year`
- **Description:** Counts the number of wet months within each calendar year.
- **Grain:** Annual (derived by explicitly constructing monthly context).
- **Purpose:** Converts precipitation magnitude into an interpretable frequency indicator.
- **Notes:** Monthly grain is explicitly enforced to ensure correct evaluation context.

---

---

## 🌪️ Extreme Events — Core Frequency Measures

### `Total Extreme Events`
- **Description:** Total number of extreme weather events in the dataset.
- **Grain:** Event-level (no implicit time aggregation).
- **Purpose:** Overall context, validation, and reference for composition analysis.

---

### `Extreme Events (Annual)`
- **Description:** Annual frequency of extreme weather events.
- **Grain:** Annual.
- **Logic:** Counts events while preserving only the Year context.
- **Purpose:** Primary metric for long-term extreme event trend analysis.

---

### `Extreme Events – Latest Year`
- **Description:** Number of extreme events in the most recent complete year.
- **Grain:** Annual (latest year only).
- **Purpose:** Snapshot KPI providing current context alongside long-term trends.
- **Notes:** Calendar filters are removed to ensure stability.

---

---

## 🌪️ Extreme Events — By Type

### `Extreme Precipitation Events`
- **Description:** Counts extreme events classified as heavy precipitation.
- **Grain:** Event-level.
- **Purpose:** Analyzes the frequency of precipitation-driven extreme events.

---

### `Extreme Wind Events`
- **Description:** Counts extreme events classified as extreme wind.
- **Grain:** Event-level.
- **Purpose:** Analyzes the frequency of wind-driven extreme events.

---

### `Total Extreme Events by Type`
- **Description:** Total number of extreme events within the current event type context.
- **Grain:** Event-level.
- **Purpose:** Absolute composition analysis by category.
- **Important:** Requires event type to be present in the visual.

---

### `Extreme Event Share (%)`
- **Description:** Proportion of extreme events by event type.
- **Logic:** Event count in current context divided by total event count.
- **Purpose:** Composition analysis (e.g., precipitation vs wind events).

---

### `Pct Province Extreme Events`
- **Description:** Share of total extreme events attributed to each province.
- **Grain:** Province-level.
- **Purpose:** Identifies regional concentration of extreme events.
- **Interpretation:** Higher values indicate greater exposure to extreme conditions.

---

---

## 📈 Extreme Events — EDA Integration

### `Total Extreme Events (Observed)`
- **Description:** Observed annual extreme event counts generated during Python EDA.
- **Source:** `ExtremeEvents_Per_Year` table.
- **Purpose:** Baseline series representing raw observed frequencies.
- **Notes:** No modelling performed in Power BI.

---

### `Extreme Events Trend (Fitted)`
- **Description:** Fitted trend values generated during Python EDA.
- **Source:** `ExtremeEvents_Per_Year` table.
- **Purpose:** Enables comparison between observed events and long-term trends.
- **Important:** Power BI acts only as visualization layer.

---

---

## 🌡️ Temperature Measures

### `Avg Monthly Temperature (°C)`
- **Description:** Average monthly temperature across all locations.
- **Grain:** Monthly.
- **Purpose:** Provides baseline temperature context for comparative analysis.

---

### `Temp Index`
- **Description:** Indexed temperature using a base year (1995 = 100).
- **Grain:** Monthly or annual.
- **Purpose:** Enables comparison of relative temperature changes over time.
- **Interpretation:** Values above 100 indicate increases relative to the base year.

---

### `Correlation Temp vs Precip`
- **Description:** Statistical correlation between temperature and precipitation indices.
- **Grain:** Annual.
- **Purpose:** Measures the strength and direction of association between variables.
- **Interpretation:** Values near zero indicate weak or no relationship.
- **Limitations:** Correlation does not imply causation.

---

---

## ✅ General Notes

- All measures are **explicit**, not implicit aggregations.
- Measures respect the **grain of their underlying datasets**.
- Power BI is used as a **consumption and integration layer**, not for statistical modelling.
- Predictive or causal modelling is handled upstream in Python.
- Results should be interpreted in a **regional and multi-factor climate context**, not as isolated relationships.
