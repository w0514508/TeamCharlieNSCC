# Python Notebooks — Danielle

## Overview

This folder contains Python notebooks used during **data acquisition, preprocessing, and exploratory data analysis (EDA)** for the precipitation and extreme weather events analysis across Atlantic Canada.

These notebooks support **methodological validation and reproducibility** and are not part of the final analytical deliverables or presentation materials.

---

## Notebook Summary

### **Extreme Event.ipynb**
Identifies daily extreme weather events using **station-specific 95th percentile (P95) thresholds**.

This notebook generates two types of extreme events:
- Extreme Wind
- Heavy Precipitation

The output is a unified, event-level dataset where each row represents a single extreme event. Event magnitudes are standardized into a single `EventValue` column to support consistent downstream analysis.

---

### **Pandas EDA_Extreme_Events.ipynb**
Performs exploratory data analysis (EDA) on the finalized Extreme Events dataset.

The analysis focuses on:
- Event frequency
- Distribution
- Temporal variability

This notebook was used to validate extreme event definitions and inform analytical decisions prior to building the final Power BI model.

### EDA Outputs

This exploratory analysis produced an annual aggregation of extreme event frequency, used to validate temporal trends and support downstream BI reporting. These outputs are treated as frozen analytical artifacts.

---

### **Precipitation Cleaning.ipynb**
Prepares monthly precipitation data obtained from Environment and Climate Change Canada (ECCC) for analysis.

Scope:
- Region: Atlantic Canada (NS, NB, PE, NL)
- Period: 1995–2025
- Granularity: Monthly
- Metric: Total Monthly Precipitation (mm)

The output of this notebook is a cleaned precipitation fact table used for Power BI integration.

---

### 🌡️ Monthly_Temperature.ipynb

- **Description:** Python notebook used to process and structure monthly temperature data at the station level.
- **Purpose:** Transforms raw temperature data into a clean, analysis-ready dataset.
- **Output:** Generates `monthly_temperature_by_station.csv`.
- **Key Steps:**
  - Data cleaning and formatting  
  - Construction of Year / Month / YearMonth structure  
  - Calculation of mean monthly temperature (`MeanMonthlyTemp_C`)  
- **Notes:** Acts as a preprocessing step; results are later integrated into Power BI for analysis.

---

### **Script for raw data download.ipynb**
Utility notebook used to download raw climate data files from Environment and Climate Change Canada.

This notebook supports data acquisition and reproducibility but is not directly tied to analytical outputs or visualizations.

---

## Notes

- The notebooks in this folder are exploratory and operational in nature.
- Final datasets generated through these notebooks are stored in `data/clean/Danielle`.
- Visualizations and findings are implemented exclusively in the Power BI (PBIX) model.
