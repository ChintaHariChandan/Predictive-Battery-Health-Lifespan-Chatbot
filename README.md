# Predictive-Battery-Degradation-Chatbot
*A Generative AI + Machine Learning System for Intelligent EV Battery Management*

## 🧠 Overview

The **Predictive Battery Degradation Chatbot** is an **AI-powered assistant** designed to forecast Electric Vehicle (EV) battery **Degradation Rate (%)** using **real-world telemetry data**.  

It seamlessly integrates **Predictive Machine Learning Models** with a **Generative AI Chatbot** to provide:  
- 🤖 **Human-like explanations** of battery health and degradation patterns  
- ⚡ **Personalized tips** to extend battery lifespan  
- 🔍 **Actionable insights** for proactive maintenance and performance optimization  

This fusion of **ML + Generative AI** empowers users with both accurate predictions and intuitive guidance — making EV battery management smarter and more efficient.

---

## 🌍 Project Motivation
Battery degradation is one of the key challenges in electric mobility.  
Traditional Battery Management Systems (BMS) monitor parameters but **lack predictive intelligence and user interpretability**.  
This project aims to:
- Predict **health degradation** using machine learning.
- Provide **personalized conversational insights** through a Generative AI chatbot.
- Promote **sustainable EV usage** by helping users optimize charging and driving habits.

---

## 📊 Dataset — EVIoT-PredictiveMaint (Kaggle)
**Source:** [EV_battery_charging_data Dataset – Kaggle](https://www.kaggle.com/datasets/ziya07/ev-battery-charging-data)  

| Feature | Description |
|:--|:--|
| **Charging Duration (min)** | Total charging time in minutes |
| **SOC (%)** | State of Charge — the current battery charge percentage |
| **Battery Temp (°C)** | Battery temperature during operation |
| **Optimal Charging Duration Class** | Categorized charging behavior (Optimal / Non-Optimal) |
| **Degradation Rate (%)** | Target variable representing the rate of battery degradation |

## ⚙️ Data Preprocessing
Steps performed before model training:
1. **Data Cleaning**
   - Removed duplicates, missing, or invalid entries.
2. **Feature Encoding**
   - Converted categorical columns into numerical format using Label Encoding.
3. **Outlier Handling**
   - IQR-based method to identify and limit outliers.
4. **Feature Scaling**
   - StandardScaler applied for uniform feature contribution.
5. **Train-Test Split**
   - 80% training and 20% testing ratio for evaluation.

---

## 🤖 Machine Learning Model
A **Random Forest Regressor** was implemented due to its robustness and ability to capture nonlinear feature relationships.

### **Model Configuration**
RandomForestRegressor(
    n_estimators=200,
    random_state=42
)

## 🤖 Evaluation Metrics
| Metric | Description | Result |
|:--|:--|:--|
| **R² Score** | Proportion of variance explained by the model | 0.9934 |
| **MSE** | Mean Squared Error — average squared prediction error | 0.0426 |
| **MAE** | Mean Absolute Error — average absolute prediction error | 0.1587
| **Z- Score** | Measures deviation of residuals | 0.8218

### 🔍 Feature Importance Analysis

| Rank | Feature                      | Importance | Insight                                      |
|------|------------------------------|-------------|----------------------------------------------|
| 1️⃣  | Charging Duration (min)      | 0.78        | Long charge duration increases degradation   |
| 2️⃣  | SOC (%)                      | 0.21        | Higher SOC mildly increases degradation      |
| 3️⃣  | Battery Temp (°C)            | 0.0075      | Temperature affects chemical stability       |
| 4️⃣  | Optimal Charging Duration Class | 0.0016   | Minimal influence                            |

### 🔍 Results Summary

- **R² Score:** 0.9934 → Indicates strong predictive accuracy.  
- **MSE / MAE:** Extremely low values, confirming excellent generalization.  
- **Model Performance:** Demonstrates high consistency between predicted and actual degradation rates.  
- **Physical Insights:**  
  - Longer charging durations accelerate battery degradation.  
  - Higher SOC levels contribute moderately to degradation.  
  - Battery temperature has a minor but noticeable effect on chemical stability.  
  - Optimal charging class shows minimal influence on degradation behavior.  

### 🛠️ Tech Stack

- **Language:** Python 🐍  
- **Libraries:**  
  - pandas  
  - numpy  
  - matplotlib  
  - seaborn  
  - scikit-learn  
- **Model Used:** Random Forest Regressor 🌲  
- **Development Tools:**  
  - Jupyter Notebook  


## 👤 Author    
Chinta Harichandan    
📧 Email: harichandan130505@gmail.com  
🔗 LinkedIn Profile: https://www.linkedin.com/in/harichandan-chinta-210451346  
📂 GitHub: https://github.com/ChintaHariChandan  

## 📜 License
This project is licensed under the MIT License – feel free to use, modify, and distribute.
