# NSCC Capstone Project
## Environment & Climate Analytics Dashboard
**Team Charlie**

---

## Project Overview

This repository contains the deliverables, documentation, datasets, and analytical workflows for **Team Charlie’s NSCC Capstone Project on Environment & Climate Analytics**.

The project investigates **long‑term environmental and climate patterns in Atlantic Canada**, with a focused analytical lens on **Nova Scotia**. Using open data published by **Environment and Climate Change Canada (ECCC)** and other federal sources, the team applies **ETL, exploratory data analysis (EDA), statistical modeling, and Business Intelligence (BI)** techniques to transform raw environmental datasets into **interactive Power BI dashboards**.

The dashboard integrates **temperature, precipitation, extreme weather events, greenhouse gas (GHG) emissions, and air quality (AQI)** to support trend analysis, anomaly detection, and short‑term forecasting.

---

## Project Objectives

- Analyze **30‑year historical trends (≈1995–2025)** in:
  - Average temperature  
  - Precipitation  
  - Extreme weather events
- Identify and quantify **climate anomalies** relative to 30‑year baselines
- Evaluate whether **extreme weather event frequency** is increasing in Nova Scotia
- Compare **GHG emissions trends** across provinces and sectors
- Analyze **Air Quality Index (AQI)** trends and their correlation with meteorological conditions
- Develop a **5‑year temperature forecast** for selected Nova Scotia weather stations
- Deliver **interactive, insight‑driven Power BI dashboards**

---

## Data Sources

This project uses authoritative, publicly available datasets published by federal and provincial agencies. These sources provide historical climate observations, emissions inventories, and air quality metrics used for long‑term trend analysis, anomaly detection, and forecasting.

### Climate, Temperature & Precipitation

- **Environment and Climate Change Canada (ECCC) – Daily Climate Observations**  
  Station‑level daily climate data (temperature, precipitation, wind, snow) in CSV format, accessed by province, Climate ID, and year.  
  https://dd.weather.gc.ca/today/climate/observations/
- **Technical Documentation by ECCC**
  https://climate.weather.gc.ca/doc/Technical_Documentation.pdf

- **ECCC – Historical Climate Data Portal**  
  Official portal for historical station records, climate summaries, and validated climate normals.  
  https://climate.weather.gc.ca/

- **Canadian Centre for Climate Services – Climate Data Access**  
  Centralized access to historical climate datasets, metadata, and documentation used for baseline and anomaly analysis.  
  https://www.canada.ca/en/environment-climate-change/services/climate-change/canadian-centre-climate-services/display-download/climate-data.html

---

### Greenhouse Gas (GHG) Emissions

- **Canadian Environmental Sustainability Indicators (CESI) – Greenhouse Gas Emissions**  
  Annual provincial and national GHG emissions data by economic sector.  
  https://www.canada.ca/en/environment-climate-change/services/environmental-indicators/greenhouse-gas-emissions.html

- **Government of Canada Open Data – National GHG Inventory**  
  Machine‑readable datasets supporting province‑level and sector‑level emissions analysis.  
  (https://www150.statcan.gc.ca/t1/tbl1/en/tv.action?pid=3810009701&cubeTimeFrame.startYear=2013&cubeTimeFrame.endYear=2023&referencePeriods=20130101%2C20230101)

---

### Air Quality Index (AQI)

- **Environment and Climate Change Canada – Air Quality Health Index (AQHI)**  
  National AQI datasets and health‑based index documentation.  
  https://www.canada.ca/en/environment-climate-change/services/air-quality-health-index.html

- **Government of Canada Open Data – Air Quality Datasets**  
  - Open station‑level air quality measurements used for AQI trend and exceedance analysis.  
  - https://search.open.canada.ca/opendata/?search_text=air+quality
  - https://data-donnees.az.ec.gc.ca/data/air/monitor/national-air-pollution-surveillance-naps-program?lang=en

---

## ETL & Data Preparation Overview

### Station Selection for Temperature and Precipitation

- A cleaned station reference file (**stationlist_clean.csv**) is used as the control input.
- Stations are filtered to **Atlantic Canada**:
  - Nova Scotia (NS)
  - New Brunswick (NB)
  - Prince Edward Island (PE)
  - Newfoundland and Labrador (NL)
- Only stations with:
  - Valid **Climate IDs**
  - Recent operational history  
    are retained.

✅ **137 active Atlantic Canada weather stations** are used in the analysis.

---

### Climate Daily Data Integration

- Daily climate data is downloaded using **province‑specific ECCC CSV endpoints**.
- Coverage:
  - **Start year:** 1995
  - **End year:** Current runtime year
- Granularity:
  - Province × Climate ID × Year

✅ **2,730 daily CSV files** were ingested and consolidated.

---

### Final Climate Dataset

After cleaning and consolidation:

- **997,119 daily observations**
- Core variables include:
  - Temperature (max, min, mean)
  - Precipitation (rain, snow, total)
  - Snow on ground
  - Wind gust speed and direction
- Quality flags and non‑analytical fields are removed prior to transformation.

This dataset serves as the foundation for anomaly detection, trend analysis, and forecasting.

---

## BI Dashboard – Final Expectations

The Power BI dashboard is structured into **four topic areas**, each with defined KPIs, visuals, and analytical outputs.

---

## 1. Average Temperature Trends

**Objective:**  
Understand how temperature patterns have changed in Atlantic Canada over the past 30 years.

### Key Visuals & Metrics
- KPI Card: Average Annual Temperature (Year & Station slicers)
- Line Chart: Long‑term temperature trend
- Heatmap Calendar: Daily temperature anomalies
- Bar Chart: Year‑over‑year temperature change
- Forecast: 5‑year average annual temperature forecast for selected NS station
- Anomaly Chart: Deviation from 30‑year baseline with confidence bands

### Analytics
- Pandas EDA
- Temperature anomaly calculation
- Linear / polynomial regression
- Short‑term ARIMA/SARIMA forecasting

---

## 2. Precipitation & Extreme Weather Events

**Objective:**  
Assess long‑term precipitation patterns and extreme weather trends.

### Key Visuals & Metrics
- KPI Card: Annual Precipitation (Year & Station slicers)
- Dual‑Axis Line Chart: Temperature vs. precipitation
- Bar Chart: Year‑over‑year precipitation change
- Extreme weather frequency analysis (high wind, heavy precipitation)
- Anomaly charts with confidence bands

### Analytics
- Precipitation frequency analysis
- Extreme event trend detection
- CSV exports for Power BI ingestion

---

## 3. Greenhouse Gas (GHG) Emissions

**Objective:**  
Analyze GHG emissions changes and major contributors.

### Key Visuals & Metrics
- KPI Card: Nova Scotia GHG Change (%)
- Stacked Area Chart: Provincial emissions over time
- Bar Chart: NS emissions by sector
- Line Chart: NS vs national emissions trends

---

## 4. Air Quality Index (AQI)

**Objective:**  
Analyze AQI behavior, seasonal patterns, and meteorological correlations.

### Key Visuals & Metrics
- KPI Card: AQI Index (Year & Station slicers)
- Line Chart: AQI trends by station
- Bar Chart: Days exceeding AQI threshold by month
- Map: AQI station locations with color‑coded values
- Correlation analysis: AQI vs season, wind speed, wind direction

### Outputs
- Exported anomaly and forecast datasets for Power BI

---

## Folder Structure

```

data/
├── raw/        # Original datasets
└── clean/      # Processed datasets (by topic owner)

scripts/
├── python/     # ETL, EDA, modeling
└── sql/        # SQL transformations

docs/            # Documentation and data dictionaries
reports/         # Final reports and dashboards

```

---

## Team Members & Responsibilities

**Team Charlie**

- **Yashaswi Tiwari**  
  Project Manager  
  Owner: Average Temperature Analysis  
  AQI Ownership (post 1 May 2026)

- **Danielle Aranha**  
  Data Lead & SQL/ETL Analyst  
  Owner: Precipitation & Extreme Weather Events

- **Michael Okafor**  
  Reporting Lead & SQL/ETL Analyst  
  Owner: GHG Emissions

- **Chisom Njoku**  
  SQL/ETL Analyst  
  Owner: AQI (until 1 May 2026)

- **Tracy Odaro**  
  QA and Documentation

---

## Tools & Technologies

- Python (Pandas, NumPy, scikit‑learn, statsmodels)
- SQL
- Power BI
- GitHub
- Environment and Climate Change Canada Open Data

---

## Outcome

The final deliverable is a **defensible, interactive BI dashboard** that transforms complex environmental datasets into **clear, data‑driven insights**—demonstrating the complete Business Intelligence lifecycle from **raw data to decision‑ready analytics**.
```
