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