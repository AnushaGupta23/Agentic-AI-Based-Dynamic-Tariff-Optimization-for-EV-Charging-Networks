# Agentic-AI-Based-Dynamic-Tariff-Optimization-for-EV-Charging-Networks
# AI-Powered EV Charging Network Optimization

An end-to-end analytics and machine learning framework for optimizing EV charging networks through demand prediction, dynamic tariff recommendation, and continuous monitoring.

---

## Overview

EV charging networks often experience uneven utilization, congestion during peak periods, and inefficient pricing mechanisms. This project proposes a three-agent framework that combines predictive analytics and rule-based optimization to improve operational efficiency.

The system focuses on:

* Demand forecasting
* Dynamic tariff recommendation
* Monitoring and performance evaluation

The approach follows the requirements specified in OP'26 Analytics and avoids unnecessary complexity such as reinforcement learning or large language model agents.

---

## Problem Statement

EV charging stations experience:

* Demand imbalance across locations
* Peak-hour congestion
* Underutilized infrastructure
* Static pricing policies

The objective is to build an explainable AI framework that can:

1. Predict charging demand.
2. Recommend tariff adjustments.
3. Continuously monitor network performance.

---

## Dataset

### ACN Dataset

Contains charging session information:

* Connection time
* Session duration
* Energy delivered
* Site information
* Station identifiers

### UrbanEV Dataset (ST-EVCDP)

Contains operational information for 247 charging stations and more than 2.13 million observations.

Main tables include:

* Volume
* Occupancy
* Duration
* Price
* Distance
* Station metadata
* Time information
* Adjacency matrix
* Station information

---

## Feature Engineering

The following operational features were created:

* Utilization Rate
* Occupancy Density
* Revenue
* Energy Cost per kWh
* Queue Length Proxy
* Dynamic Pricing Flag
* CBD Indicator
* Temporal Features

Additional time features:

* Hour
* Day of Week
* Month
* Weekend Indicator

---

## Exploratory Data Analysis

Analysis focused on:

* Long-run demand patterns
* Utilization fluctuations
* Peak and off-peak charging behavior
* Weekday versus weekend demand
* Geographical differences
* Pricing implications

Major findings:

* Average utilization ≈ 28%
* Demand is concentrated in a subset of stations
* Dynamic pricing stations experience higher demand
* Charging behavior varies across CBD and non-CBD regions

---

## System Architecture

```
                    ┌─────────────────┐
                    │  Demand Agent   │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │ Pricing Agent   │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │ Monitoring Agent│
                    └─────────────────┘
```

---

## Agent 1: Demand Prediction Agent

### Objective

Predict:

* Charging load
* Utilization rate
* Congestion probability

### Features

* Hour
* Month
* Day of Week
* Occupancy
* Price
* Station ID
* Duration
* CBD indicator

### Models

* Linear Regression
* Random Forest Regressor
* XGBoost

### Evaluation Metrics

* MAE
* RMSE
* R² Score

---

## Agent 2: Dynamic Tariff Pricing Agent

A rule-based pricing mechanism adjusts tariffs based on predicted utilization.

### Pricing Logic

```python
if predicted_utilization > 0.80:
    tariff = base_price * 1.25

elif predicted_utilization < 0.30:
    tariff = base_price * 0.90

else:
    tariff = base_price
```

### Outputs

* Tariff category
* Revenue estimates
* Utilization improvement
* Off-peak demand uplift

---

## Agent 3: Monitoring and Learning Agent

Tracks:

* Revenue
* Utilization
* Congestion
* Queue proxy
* Pricing efficiency

The monitoring layer evaluates system performance and generates operational alerts.

---

## Project Structure

```
project/
│
├── data/
│
├── notebooks/
│   ├── 01_data_ingestion.ipynb
│   ├── 02_acn_eda.ipynb
│   ├── 03_urbanev_eda.ipynb
│   ├── 04_demand_prediction_agent.ipynb
│   ├── 05_tariff_pricing_agent.ipynb
│   └── 06_monitoring_learning_agent.ipynb
│
├── agents/
│
├── outputs/
│   ├── predictions.csv
│   ├── tariffs.csv
│   ├── monitoring_metrics.csv
│   └── final_outputs.csv
│
├── presentation/
│
└── README.md
```

---

## Technologies Used

### Data Processing

* Pandas
* NumPy

### Visualization

* Matplotlib
* Seaborn
* Plotly

### Machine Learning

* Scikit-Learn
* XGBoost
* Random Forest

---

## Results

The framework aims to achieve:

* Accurate demand forecasting
* Improved station utilization
* Reduced congestion
* Revenue enhancement through dynamic pricing
* Continuous operational monitoring

---

## Future Work

* Real-time deployment
* Weather-aware demand forecasting
* Grid-aware optimization
* Reinforcement learning-based pricing
* Multi-city validation

---

## Conclusion

This project demonstrates how an integrated three-agent analytics framework can improve EV charging network efficiency through demand prediction, dynamic tariff recommendation, and continuous monitoring. The solution is designed to be explainable, scalable, and aligned with practical operational requirements.

---
