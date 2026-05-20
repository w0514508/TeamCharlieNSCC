# 📘 Data Dictionary — Temperature (Monthly)

This document describes the structure and meaning of the temperature dataset used in the Power BI model.

The dataset provides **monthly temperature observations per station**, supporting time-series analysis and integration with precipitation and extreme event data.

---

## 📊 Dataset Overview

- **Source:** Monthly temperature data by weather station  
- **Granularity:** Station × Month  
- **Time Range:** 1995–2025  
- **Key Metric:** Mean Monthly Temperature (°C)  

---

## 🔑 Fields Description

---

### `Climate ID`
- **Type:** Integer / Text (Identifier)  
- **Description:** Unique identifier for each weather station.  
- **Grain:** Station-level  
- **Purpose:** Links temperature records to station-level metadata.  
- **Notes:** Used for joins with station and geographic dimension tables.

---

### `Year`
- **Type:** Integer  
- **Description:** Calendar year of the recorded observation.  
- **Grain:** Year-level  
- **Purpose:** Supports annual aggregation and time-based analysis.  

---

### `Month`
- **Type:** Integer (1–12)  
- **Description:** Numeric representation of the calendar month.  
- **Grain:** Month-level  
- **Purpose:** Enables monthly grouping and seasonal analysis.  

---

### `YearMonth`
- **Type:** Text (YYYY-MM)  
- **Description:** Combined year and month identifier.  
- **Grain:** Monthly  
- **Purpose:** Simplifies chronological ordering and time-series visualization.  
- **Notes:** Often used for plotting trends without requiring full date formatting.

---

### `MeanMonthlyTemp_C`
- **Type:** Decimal (°C)  
- **Description:** Average temperature recorded for the station during the given month.  
- **Grain:** Station × Month  
- **Purpose:** Core temperature metric used for:
  - Trend analysis  
  - Index calculations  
  - Correlation with precipitation  
- **Interpretation:** Represents mean temperature, not extremes (min/max).  

---

## 🔄 Data Behavior & Analytical Notes

- Temperature is recorded at a **monthly resolution**, not daily.
- Each station contributes **one value per month**, ensuring consistency across time.
- Data supports:
  - Temporal analysis (trends, variability)
  - Spatial comparisons (across stations/provinces)
  - Integration with precipitation and extreme events

---

## ⚠️ Limitations

- Does **not capture temperature extremes** (only mean values)
- Assumes consistent station data availability over time
- Seasonal patterns are present but must be interpreted separately from long-term trends

---

## ✅ Usage in the Model

This dataset is primarily used to:

- Build **temperature indices** for relative comparison  
- Compare temperature patterns with precipitation  
- Support **correlation analysis**  
- Provide environmental context for extreme events  
