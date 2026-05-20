# 📁 Clean Data — Danielle

This folder contains the cleaned and prepared datasets used in the Climate Analysis dashboard.

All datasets are structured to support integration in a Power BI star schema, enabling consistent time-series analysis across precipitation, temperature, and extreme events.

---

## 📊 Available Datasets

---

### 🌧️ `monthly_precipitation_by_station.csv`

#### Description
Monthly precipitation observations at the station level.

#### Granularity
- Station × Month

#### Key Fields
- Climate ID  
- Date / Year / Month  
- Precipitation (mm)  

#### Purpose
- Core dataset for precipitation analysis  
- Supports:
  - Monthly trends  
  - Annual aggregation  
  - Variability and anomaly analysis  

---

### 🌡️ `monthly_temperature_by_station.csv`

#### Description
Monthly average temperature recorded for each weather station.

#### Granularity
- Station × Month

#### Key Fields
- Climate ID  
- Year  
- Month  
- YearMonth  
- MeanMonthlyTemp_C  

#### Purpose
- Provides temperature context for climate analysis  
- Supports:
  - Temperature trend analysis  
  - Index calculations (base year comparison)  
  - Correlation with precipitation  

#### Notes
- Data reflects **mean monthly temperature**, not extremes  
- Used primarily for comparative analysis, not standalone risk assessment  

---

### 🌪️ `extreme_events.csv`

#### Description
Event-level dataset containing records of extreme weather events.

#### Granularity
- Event-level

#### Key Fields
- Event Type  
- Date / Year  
- Location / Province  

#### Purpose
- Measures frequency of extreme events  
- Supports:
  - Annual trend analysis  
  - Event type breakdown (precipitation vs wind)  
  - Regional comparisons  

---

### 📈 `ExtremeEvents_Per_Year.csv`

#### Description
Aggregated and model-enhanced dataset generated during Python EDA.

#### Granularity
- Year

#### Key Fields
- Year  
- EventCount (Observed)  
- Fitted (Trend)

#### Purpose
- Compare observed extreme events with fitted trend  
- Provide smoothed representation of long-term behavior  

#### Important
- Fitted values are:
  - Generated in Python (not Power BI)  
  - Based on historical trends only  
  - Intended for visualization, not prediction  

---

## 🧠 Data Integration

These datasets are integrated into the Power BI model through:

- `Dim_Calendar` → time alignment  
- `Dim_Station` → geographic alignment  

This enables:

- Cross-variable comparison (temperature vs precipitation)  
- Trend analysis across time  
- Regional aggregation  

---

## ⚠️ Assumptions & Limitations

- Data is primarily **monthly or yearly aggregated**
- Temperature reflects **mean values only**
- Extreme events data:
  - Captures frequency, not severity  
- Fitted trend is:
  - Descriptive  
  - Not predictive  

---

## ✅ Usage

These datasets are used to:

- Build analytical measures (DAX)
- Support visualizations in Power BI
- Provide context for climate variability and risk assessment

