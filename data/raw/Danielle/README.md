# Raw Data — Danielle

## Overview

This folder contains **raw and intermediate climate data files** used as upstream inputs for the generation of cleaned and analysis-ready datasets related to **precipitation and extreme weather events** across Atlantic Canada.

The files in this directory are **not used directly for analysis or visualization**.  
They are retained for data lineage, traceability, and reproducibility of the processing pipeline.

---

## Contents

### ✅ fact_Atlantic_Climate.zip

Compressed raw daily climate dataset derived from Environment and Climate Change Canada observations.

This dataset includes daily measurements for multiple climate variables (e.g., precipitation, wind, temperature) at the station level.

The file is retained for **reference, traceability, and reproducibility**, particularly to document the original daily observations underlying climate indicators such as precipitation and extreme events.

This dataset is **not used directly** to generate the monthly precipitation tables included in this project, as monthly aggregates were obtained directly from Environment and Climate Change Canada.

---

### ✅ precipitation_monthly_raw_atlantic.csv

Intermediate dataset containing **monthly aggregated precipitation values** derived from daily climate observations across Atlantic Canada.

This file represents a preprocessing step between raw daily climate data and the final cleaned precipitation fact table.

- Granularity: one row per station per month
- Units: millimeters (mm)

This dataset is not used directly in presentation or visualization and exists to support validation and traceability.

---
### 🌡️ dim_temp_clean.zip

- **Description:** Raw cleaned dataset containing temperature records at the station level.
- **Granularity:** Station-level observations (pre-aggregation).
- **Purpose:** Source dataset used to create the structured monthly temperature table.
- **Output:** Used to generate `monthly_temperature_by_station.csv`.
- **Notes:** Contains intermediate temperature data and is not used directly in the final Power BI model.

## Notes

- Raw daily data is preserved in compressed or intermediate form only.
- Final, analysis-ready datasets are stored in `data/clean/Danielle`.
- Dataset definitions and analytical assumptions are documented in `docs/Danielle`.

---

## Relationship to Clean Data

Processed datasets generated from these raw inputs include:
- Monthly precipitation fact table
- Monthly temperature fact table
- Extreme weather events fact table

Refer to `data/clean/Danielle/README.md` for details on cleaned datasets and analytical usage.
