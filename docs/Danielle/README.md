# 🌦️ Climate Analysis Dashboard — Atlantic Canada

## 📊 Project Overview

This project analyzes precipitation trends and climate-related variables in Atlantic Canada, with the goal of providing insights that support decision-making in areas such as planning, risk management, and operations.

The analysis integrates multiple environmental datasets to explore how precipitation behaves over time and how it relates to other indicators such as temperature, extreme weather events, and emissions.

---

## 🎯 Objective

The primary objective of this project is to:

- Analyze long-term precipitation trends  
- Identify changes in variability and extreme events  
- Evaluate relationships between precipitation and other environmental indicators  
- Provide a clear and actionable interpretation of climate patterns  

---

## 📦 Datasets Used

This project integrates multiple datasets, each documented separately:

- 🌧️ **Precipitation (Monthly)**  
- 🌡️ **Temperature (Monthly)**  
- 🌪️ **Extreme Events (Event-level)**  
- 📈 **Extreme Events (EDA Output — Python)**  

Each dataset includes detailed data dictionaries:

- Data Dictionary — Precipitation  
- Data Dictionary — Temperature  
- Data Dictionary — Extreme Events  
- Data Dictionary — Extreme Events (EDA Output)  

---

## 🧱 Data Model

The model follows a **star schema structure**, integrating multiple fact tables:

### Fact Tables:
- `Fact_Precipitation_Monthly`
- `Fact_Temperature_Monthly`
- `Fact_Extreme_Events`
- `ExtremeEvents_Per_Year` (EDA output)

### Dimension Tables:
- `Dim_Calendar`
- `Dim_Station`

The model is designed to support:
- Time-based analysis  
- Cross-variable comparison  
- Regional aggregation  

A conceptual schema is documented in:

- 📘 Data Dictionary — Climate & Environmental Star Schema  

---

## 🧠 Analytical Approach

The project is structured around three main analytical dimensions:

### 1. Trend & Growth
- Long-term increase in precipitation
- Identification of structural changes over time

### 2. Variability & Uncertainty
- High monthly variability (~57%)
- Increased unpredictability in precipitation patterns

### 3. Relationships Across Variables
- Weak or inconsistent relationships between:
  - Precipitation and temperature  
  - Precipitation and GHG emissions  
  - Precipitation and air quality  

---

## 🌪️ Extreme Events Analysis

Extreme weather events are analyzed across two layers:

### Observed Data
- Event-level dataset  
- Annual frequency of extreme events  

### EDA Output (Python)
- Smoothed trend (fitted series)  
- Used for comparing observed vs long-term patterns  

Power BI is used strictly as a visualization layer for these results.

---

## 🧩 Analytical Summary Layer

A manually created summary table integrates key findings across provinces.

This layer:

- Combines multiple variables into a simplified structure  
- Highlights regional differences  
- Shows that relationships across variables are **not consistent**  

This table is documented as:

- 📘 Analytical Summary Table — Climate Relationships  

---

## 📐 Measures & Calculations

All analytical calculations are implemented using explicit DAX measures, including:

- Aggregation measures (totals and averages)  
- Trend indicators (YoY change, long-term trends)  
- Variability metrics  
- Index-based comparisons  
- Correlation analysis  

Full documentation available in:

- 📘 DAX Measure Dictionary — Precipitation, Temperature & Extreme Events  

---

## ⚠️ Assumptions & Limitations

- Climate relationships are **non-linear and multi-factor**  
- No causal relationships are assumed between variables  
- Data is aggregated at monthly or yearly levels  
- Temperature data reflects averages, not extremes  
- Fitted trends from EDA are descriptive, not predictive  

---

## 💡 Key Insights

- Precipitation in Atlantic Canada is **increasing over time**  
- Extreme events are **more frequent and more intense**  
- Precipitation shows **high variability (~57%)**, indicating instability  
- There is **no consistent relationship** between precipitation and:
  - Temperature  
  - GHG emissions  
  - Air quality  

---

## 🧰 Tools & Technologies

- **Power BI** — Dashboard and data modeling  
- **DAX** — Analytical calculations  
- **Python (EDA)** — Trend fitting and data exploration  
- **GitHub** — Documentation and version control  

---

## 👥 Team

This project was developed collaboratively, with each member focusing on a specific analytical component:

- Precipitation & Extreme Events  
- Temperature & Air Quality  
- GHG Emissions  

The final dashboard integrates all components into a unified analytical view.

---

## ✅ Conclusion

This analysis shows that precipitation patterns in Atlantic Canada are:

- Increasing  
- More variable  
- More extreme  

At the same time, these patterns are **not explained by a single environmental factor**, highlighting the complexity of climate systems and the importance of multi-variable analysis.

---
