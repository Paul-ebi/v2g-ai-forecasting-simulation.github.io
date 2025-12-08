---
title: "Step 1 — Data Preprocessing"
nav_order: 2
---

# Step 1 — Data Preprocessing

This section documents how EV, Load, and PV datasets were cleaned, aligned, and made ready for AI forecasting and MATLAB simulation.

---

## ⭐ Objectives
- Convert datasets to a **uniform 15-minute resolution**  
- Clean noise, remove impossible values  
- Generate EV availability time series  
- Produce final datasets:  
  - `clean_load_data_15min.csv`  
  - `clean_solar_data_15min.csv`  
  - `clean_ev_data_15min.csv`

---

## 1️⃣ Load Data Cleaning
- Removed rows containing null load values  
- Removed years outside useful forecasting range  
- Converted to datetime index  
- Resampled to **15 min averages**  
- Clipped outliers (0.005–0.995 quantiles)  

📌 *Final range:*  
`2006–2010`

---

## 2️⃣ Solar PV Data Cleaning
- Parsed irradiance values  
- Removed negative or missing values  
- Temperature column included if available  
- Clipped extreme irradiance (0.5–99.5 percentile)  
- Converted to uniform timestamps  

📌 *Final range:*  
`2025–2025`

---

## 3️⃣ EV Session Data Cleaning
- Extracted EV charger sessions  
- Converted to continuous 15-min timeline  
- Derived new variable:

- Removed invalid charging spikes  
- Filled gaps between sessions  

📌 *Final range:*  
`2020–2021`

---

## 4️⃣ Data Consistency Check

Load range: 2006 → 2010
Solar range: 2025 → 2025
EV range:   2020 → 2021

Datasets do **not** overlap — so models are trained **independently**, not jointly.

---

## 5️⃣ Output Files

Ready for LSTM forecasting.

---