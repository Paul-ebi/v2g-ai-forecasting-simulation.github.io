---
title: "Step 2A — Load Forecasting (LSTM)"
nav_order: 3
---

# Step 2A — Load Forecasting (LSTM)

This section covers the LSTM forecasting model used for predicting community load.

---

## ⭐ Objectives
- Build a **1-step ahead** LSTM  
- Sliding window: **96 timesteps (24 hours)**  
- Predict the next 15-minute load value  
- Generate plots + performance metrics  

---

## 1️⃣ Preprocessing
- MinMax scaling of load only  
- 96-length window sequences  
- 80/20 train/test split  

---

## 2️⃣ LSTM Model Architecture

```text
Input → LSTM(128) → Dropout → LSTM(64) → Dense(32) → Dense(1)

Loss: MSE
Optimizer: Adam (0.0005)
Callbacks: EarlyStopping + ReduceLROnPlateau


3️⃣ Results

✔ Model Metrics

4️⃣ Plots

(upload your plot images to /assets/img/ and reference them)

Actual vs Predicted (First 500 samples)

![Load Forecast](assets/img/load_forecast_plot.png)

5️⃣ Interpretation
	•	Model captures short-term load trends
	•	Forecast smooths high-frequency noise
	•	Suitable as input for Step 3 — scheduling optimization

---

# 📄 **4. pv_ev_forecasting.md**

```markdown
---
title: "Step 2B — PV & EV Multi-Step Forecasting"
nav_order: 4
---

# Step 2B — PV & EV Multi-Step Forecasting (Seq2Seq LSTM)

Multi-step forecasting predicts **24 hours (96 timesteps)** ahead.

---

## ⭐ Objectives
- Seq2Seq LSTM with encoder–decoder  
- Predict next **96 samples** (24 hours)  
- Models built for:
  - Solar irradiance  
  - EV availability  

---

## 1️⃣ Architecture

```text
Encoder LSTM(128)
↓
RepeatVector(96)
↓
Decoder LSTM(64)
↓
TimeDistributed(Dense(1))

2️⃣ Solar Forecasting Results

![PV Forecast](assets/img/pv_forecast_sample.png)

3️⃣ EV Availability Forecasting Results

![EV Forecast](assets/img/ev_forecast_sample.png)

4️⃣ Interpretation
	•	EV availability forecasting performs extremely well
	•	PV irradiance is noisy and seasonal → higher error expected
	•	Forecasts feed into the MATLAB model to schedule charging

---

# 📄 **5. matlab_simulation.md**

```markdown
---
title: "Step 3 — MATLAB Simulink System Model"
nav_order: 5
---

# Step 3 — MATLAB/Simulink System Model

This section describes the physical energy system model that integrates AI forecasts into a V2G environment.

---

## ⭐ Objectives

- Build a microgrid model consisting of:
  1. PV subsystem  
  2. Load subsystem  
  3. EV charger (bidirectional)  
  4. Battery ESS  
  5. Grid import/export  
  6. AI controller input port  

---

## 1️⃣ System Architecture Diagram

[ AI Controller ] → [ EV/Battery Dispatch ]
↓
[ Forecasts ] → PV / Load / EV → Simulink Model → Grid Interaction

(Add real diagram as PNG)

---

## 2️⃣ Subsystems

### 🔹 PV Model
- Irradiance input (from Step 2)
- MPPT  
- Power clipping  
- Efficiency curves  

### 🔹 Load Model
- Time-varying load (from Step 2 output)
- Optional random fluctuations  

### 🔹 EV Charger
- Bidirectional DC  
- SOC-based dispatch  
- Efficiency + degradation modeling  

### 🔹 Battery Model
- SOC dynamics  
- Coulomb counting  
- Capacity fade  

### 🔹 Grid Model
- Import/export  
- Voltage stability  
- Frequency stability  

---

## 3️⃣ Outputs Required

- PV output  
- Load demand  
- EV SOC  
- Battery SOC  
- Grid import/export  
- Power balance  

---

## 4️⃣ Integration with Forecasting
Simulink reads:

load_forecast.csv
pv_forecast.csv
ev_forecast.csv

These guide the optimal control decisions.

---