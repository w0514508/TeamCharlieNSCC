# 📘 Data Model Documentation — Climate Data Model — Precipitation, Temperature & Extreme Events

---

## 📊 Overview

This document describes the physical data model implemented in Power BI for the Climate Analysis dashboard.

The model follows a **star schema structure**, integrating multiple fact tables to support precipitation, temperature, and extreme event analysis.

---

## 🧱 Model Structure

The model is composed of:

### Fact Tables
- `Fact_Precipitation_Monthly`
- `Fact_Temperature_Monthly`
- `Fact_Extreme_Events`
- `ExtremeEvents_Per_Year` (EDA output)

### Dimension Tables
- `Dim_Calendar`
- `Dim_Station`

---

## 🌟 Fact Tables

---

### 🌧️ Fact_Precipitation_Monthly

- **Granularity:** Station × Month  
- **Key Fields:**
  - Climate ID  
  - Date / Month / Year  
  - Precipitation_mm  

- **Purpose:**
  - Core dataset for precipitation analysis  
  - Supports:
    - Aggregation (monthly, yearly)  
    - Variability analysis  
    - Trend calculations  

---

### 🌡️ Fact_Temperature_Monthly

- **Granularity:** Station × Month  
- **Key Fields:**
  - Climate ID  
  - Year / Month / YearMonth  
  - MeanMonthlyTemp_C  

- **Purpose:**
  - Provides temperature context  
  - Supports:
    - Temperature index calculations  
    - Correlation with precipitation  

- **Notes:**
  - Contains average temperature (no extremes)

---

### 🌪️ Fact_Extreme_Events

- **Granularity:** Event-level  
- **Key Fields:**
  - EventType  
  - Date / Year  
  - Province / Location  

- **Purpose:**
  - Tracks frequency of extreme events  
  - Supports:
    - Annual trends  
    - Composition analysis (by event type)

---

### 📈 ExtremeEvents_Per_Year

- **Granularity:** Year  
- **Key Fields:**
  - Year  
  - EventCount  
  - Fitted  

- **Purpose:**
  - Provides aggregated and modeled trend data  
  - Used for:
    - Comparing observed vs trend values  

- **Notes:**
  - Generated in Python (EDA phase)  
  - Not part of transactional data  

---

## 📐 Dimension Tables

---

### 📅 Dim_Calendar

- **Grain:** Daily (or monthly, depending on implementation)  
- **Key Fields:**
  - Date  
  - Year  
  - MonthNumber  
  - MonthStartDate  

- **Purpose:**
  - Central time dimension  
  - Enables:
    - Time intelligence (YoY, trends)
    - Alignment across datasets  

---

### 📍 Dim_Station

- **Grain:** Station-level  
- **Key Fields:**
  - Climate ID  
  - ProvinceCode  
  - Location attributes  

- **Purpose:**
  - Provides geographic context  
  - Enables region-based filtering and aggregation  

---

## 🔗 Relationships

The model is centered around shared dimensions:

### Key Relationships

- `Fact_Precipitation_Monthly[Climate ID]` → `Dim_Station[Climate ID]`
- `Fact_Temperature_Monthly[Climate ID]` → `Dim_Station[Climate ID]`

- `Fact_Precipitation_Monthly[Date]` → `Dim_Calendar[Date]`
- `Fact_Temperature_Monthly[Date]` → `Dim_Calendar[Date]`
- `Fact_Extreme_Events[Date/Year]` → `Dim_Calendar`

- `ExtremeEvents_Per_Year[Year]` → `Dim_Calendar[Year]`

---

## 🧠 Design Rationale

The model was designed to:

- Maintain **separation of concerns** between datasets  
- Support **multi-variable analysis**  
- Enable **consistent time alignment** across all measures  
- Avoid duplication of attributes  

---

## ⚠️ Limitations

- Some datasets exist at different grains:
  - Monthly (precipitation, temperature)  
  - Event-level (extreme events)  
  - Annual (EDA output)

- Relationships rely on:
  - Consistent calendar alignment  
  - Station-to-province mapping  

- EDA dataset is:
  - Static  
  - Not dynamically recalculated in Power BI  

---

## ✅ Usage in Analysis

This model supports:

- Trend analysis  
- Variability and anomaly calculations  
- Cross-variable comparisons  
- Regional and temporal aggregation  
