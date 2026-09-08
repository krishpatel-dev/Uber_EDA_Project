# 🚗 Uber Supply-Demand Gap: Exploratory Data Analysis (EDA)

![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-3776AB?style=for-the-badge)
![Plotly](https://img.shields.io/badge/Plotly-Interactive%20Charts-3F4F75?style=for-the-badge&logo=plotly&logoColor=white)

---

## 📌 Project Overview

This repository presents an in-depth **Exploratory Data Analysis (EDA)** on the **Uber Supply-Demand Gap**. Uber Technologies, Inc. is the world's largest ride-hailing platform, coordinating over 28 million trips daily across 70 countries. However, driver cancellations and unfulfilled ride requests at critical transit hubs (e.g., airports and city centers) lead to revenue loss and reduced customer satisfaction.

The objective of this project is to analyze ride request patterns, identify the core bottlenecks causing supply-demand gaps between **City** and **Airport** routes across different times of the day, and formulate data-driven business recommendations to optimize fleet distribution and revenue.

---

## 🎯 Business Objectives

1. **Driver Cancellation Identification:** Uncover the underlying reasons behind driver ride cancellations during specific time slots and routes.
2. **Supply Deficit Resolution:** Pinpoint key time windows where ride demand exceeds driver availability ("No Cars Available").
3. **Customer Satisfaction & Transparency:** Identify solutions to reduce wait times and improve ride completion rates for airport commuters.
4. **Fleet & Pricing Optimization:** Recommend actionable operational strategies (e.g., incentives, fleet rebalancing, penalty policies) to increase trip completion rates and driver efficiency.

---

## 📊 Dataset Profile

The dataset (`Uber Request Data.csv`) contains **6,745 ride request records** with 6 key features:

| Field Name | Data Type | Description |
| :--- | :--- | :--- |
| `Request id` | Integer | Unique identification number for every ride request |
| `Pickup point` | String | Location where the ride was requested (`Airport` or `City`) |
| `Driver id` | Float / String | Unique identifier assigned to the driver (`NaN` if no driver accepted) |
| `Status` | String | Status of the request (`Trip Completed`, `Cancelled`, `No Cars Available`) |
| `Request timestamp` | Datetime / String | Timestamp when the user requested the cab |
| `Drop timestamp` | Datetime / String | Timestamp when the trip was completed (`NaN` for unfulfilled trips) |

---

## 🔎 Key Findings & Analytical Insights

```
                   Trip Completion Breakdown (Total: 6,745 Requests)
   ┌───────────────────────────┬─────────────┬─────────────┐
   │ Status                    │ Count       │ Percentage  │
   ├───────────────────────────┼─────────────┼─────────────┤
   │ Trip Completed            │ 2,831       │  41.97%     │
   │ No Cars Available         │ 2,650       │  39.29%     │
   │ Cancelled                 │ 1,264       │  18.74%     │
   └───────────────────────────┴─────────────┴─────────────┘
```

> ⚠️ **Critical Gap:** Unfulfilled demand (**No Cars Available** + **Cancelled**) accounts for **58.03%** of all customer requests.

### 1. The Airport Dilemma (Evening Peak Shortage)
- **Primary Issue:** **Severe Car Shortage** (`No Cars Available`).
- **Data Highlight:** Out of 3,238 airport requests, **1,713 (52.9%)** resulted in "No Cars Available".
- **Time Slot:** Peak bottleneck occurs during the **Evening/Night hours (5:00 PM – 10:00 PM)**.
- **Root Cause:** Flights frequently arrive in evening blocks, leading to massive surges in airport-to-city demand. Drivers avoid idling at the airport during late hours due to long queue wait times.

### 2. The City Dilemma (Morning Peak Cancellations)
- **Primary Issue:** **High Driver Cancellation Rate** (`Cancelled`).
- **Data Highlight:** Out of 3,507 city requests, **1,066 (30.4%)** were cancelled by drivers (compared to only 198 cancellations at the airport).
- **Time Slot:** Peak cancellations occur during **Early Morning hours (5:00 AM – 10:00 AM)**.
- **Root Cause:** Commuters book rides to the airport for early flights. Drivers cancel these rides because the probability of securing a return trip from the airport back to the city during late morning is extremely low, making the trip financially inefficient.

---

## 💡 Strategic Business Recommendations

1. **Airport Fleet Staging & Predictive Rebalancing:**
   - Pre-position driver fleets at airport holding areas prior to peak evening flight arrival blocks (5 PM – 10 PM) using flight schedule telemetry.

2. **Return-Trip Driver Guarantees & Subsidies:**
   - Offer financial incentives or priority queue placement for drivers accepting early morning city-to-airport trips to compensate for potential empty return drives.

3. **Cancellation Thresholds & Fair Driver Policies:**
   - Implement driver penalty structures for frequent morning cancellations while increasing ride fare transparency.

4. **Premium Upselling Integration:**
   - When standard Uber rides face a "No Cars Available" state, offer dynamic discounted upgrades to **Uber Black** or **UberXL** to capture high-intent travelers.

---

## 📁 Repository Structure

```
Uber Project/
├── Uber Request Data.csv                      # Raw dataset containing 6,745 ride logs
├── Uber_Supply_Demand_Gap_EDA_Project.ipynb   # Main Jupyter notebook with complete EDA & visuals
├── .gitignore                                 # Git ignore rules for Python & Jupyter
└── README.md                                  # Comprehensive project documentation
```

---

## 🛠️ Installation & Getting Started

### Prerequisites
- **Python 3.8+**
- **Jupyter Notebook** or **JupyterLab** / **VS Code**

### 1. Clone the Repository
```bash
git clone https://github.com/krishpatel-dev/Uber_EDA_Project.git
cd Uber_Supply_Demand_EDA_Analysis
```

### 2. Create and Activate Virtual Environment
```bash
# On Windows
python -m venv venv
.\venv\Scripts\activate

# On macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install pandas numpy matplotlib seaborn plotly scikit-learn missingno wordcloud statsmodels geopandas
```

### 4. Launch Jupyter Notebook
```bash
jupyter notebook Uber_Supply_Demand_Gap_EDA_Project.ipynb
```
