# 📘 Data Dictionary — Extreme Events (EDA Output)

This document describes the structure and meaning of the extreme events dataset generated during the Python exploratory data analysis (EDA) phase.

The dataset provides a **year-level aggregation of extreme weather events**, along with a **fitted trend series** used for visualization and comparison.

---

## 📊 Dataset Overview

- **Source:** Python EDA output (`ExtremeEvents_Per_Year.csv`)
- **Granularity:** Year
- **Time Range:** 1995–2025
- **Key Metrics:**
  - Observed extreme event counts
  - Fitted trend values (model output)

---

## 🔑 Fields Description

---

### `Year`
- **Type:** Integer  
- **Description:** Calendar year of the observation.  
- **Grain:** Year-level  
- **Purpose:** Defines the time dimension for trend analysis and comparison with other datasets (temperature and precipitation).

---

### `EventCount`
- **Type:** Integer  
- **Description:** Total number of extreme weather events observed in the given year.  
- **Grain:** Annual  
- **Purpose:** Represents the raw frequency of extreme events.  
- **Usage:**
  - Baseline for trend analysis  
  - Comparison across years  
- **Interpretation:** Higher values indicate increased frequency of extreme events in a given year.

---

### `Fitted`
- **Type:** Decimal  
- **Description:** Model-derived fitted value representing the expected number of extreme events for each year.  
- **Grain:** Annual  
- **Purpose:** Provides a smoothed trend line for visualization and interpretation.  
- **Usage:**
  - Compare observed vs expected values  
  - Highlight deviations from long-term trend  
- **Important:**  
  - Generated in Python during EDA  
  - Not computed in Power BI  
  - Should be interpreted as directional, not predictive  

---

## 🔄 Data Behavior & Analytical Notes

- Observed event counts (`EventCount`) show **high variability over time**, with noticeable increases after 2010. [1](https://nscc-my.sharepoint.com/personal/w0520910_campus_nscc_ca/_layouts/15/Doc.aspx?sourcedoc=%7B66A4BCA0-9709-4557-87EA-743F62929690%7D&file=ExtremeEvents_Per_Year.csv&action=default&mobileredirect=true)  
- The fitted series provides a **smoothed representation of long-term growth**, reducing short-term fluctuations. [1](https://nscc-my.sharepoint.com/personal/w0520910_campus_nscc_ca/_layouts/15/Doc.aspx?sourcedoc=%7B66A4BCA0-9709-4557-87EA-743F62929690%7D&file=ExtremeEvents_Per_Year.csv&action=default&mobileredirect=true)  
- The dataset enables:
  - Trend analysis of extreme events  
  - Identification of structural increases  
  - Cross-comparison with precipitation and temperature patterns  

---

## ⚠️ Limitations

- Data is aggregated at the **annual level only** (no monthly or event-level detail)
- Fitted values are:
  - Based on historical trends only  
  - Not adjusted for policy, environmental, or economic changes  
- Model outputs should **not be interpreted as causal or predictive forecasts**

---

## ✅ Usage in the Model

This dataset is used in Power BI to:

- Visualize **observed vs fitted extreme event trends**  
- Support long-term climate analysis  
- Provide context for increasing variability in precipitation  
- Complement environmental indicators (temperature, GHG, AQI)  

Power BI acts strictly as a **visualization layer**, while all modelling logic is handled upstream in Python.

