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
	- Model captures short-term load trends
	- Forecast smooths high-frequency noise
	• Suitable as input for Step 3 — scheduling optimization

---