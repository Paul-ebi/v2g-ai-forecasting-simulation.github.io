---
title: "V2G AI Forecasting & Simulation"
nav_order: 1
---

# V2G AI Forecasting & Simulation 
- By Paul &  Menyhárt

A research implementation combining **AI forecasting**, **Simulink system modeling**, and **V2G optimization** for smart-grid management.

---

➡️ See: [Read Me](README.md)

## 📌 Project Components

### 1️⃣ Data Preparation (Step 1)
- Cleaned & synchronized EV, PV, and Load datasets  
- Resampled to uniform **15-minute intervals**  
- Outlier removal and null handling  
- Feature engineering: EV availability, irradiance filtering, temperature inclusion  

➡️ See: [Data Preprocessing](data_preprocessing.md)

---

### 2️⃣ AI Forecasting Layer (Step 2)
LSTM-based forecasting for:

- **Load demand** (1-step ahead)
- **PV generation** (24-step ahead)
- **EV availability** (24-step ahead)

Models:
- Sliding window: **96 timesteps (24 hours)**  
- Multi-step horizon: **96 timesteps (24 hours)**  
- Seq2Seq LSTM architecture  

➡️ See:  
- [Load Forecasting](load_forcasting.md)  
- [PV & EV Forecasting](pv_ev_forcasting.md)

---

### 3️⃣ MATLAB/Simulink Energy System Model (Step 3)
A full microgrid architecture featuring:

- PV subsystem  
- Community load subsystem  
- Bidirectional EV charger  
- Battery storage with efficiency + degradation  
- Grid import/export node  
- AI control input port  

➡️ See: [MATLAB Simulation Model](matlab_simulation.md)

---

### 4️⃣ Optimization Layer (Step 4)
Using the AI forecasts to optimize:

- Grid import cost  
- PV self-consumption  
- EV charging/discharging  
- Battery cycling  

➡️ See: [Optimization Framework](optimization.md)

---

### 5️⃣ Documentation
All diagrams, tables, methodology notes.

➡️ See: [Documentation](documentation.md)

---
