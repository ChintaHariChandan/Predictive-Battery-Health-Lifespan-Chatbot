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
|1️⃣  | Charging Duration (min)      | 0.78        | Long charge duration increases degradation   |
| 2️⃣  | SOC (%)                      | 0.21        | Higher SOC mildly increases degradation      |
| 3️⃣  | Battery Temp (°C)            | 0.0075      | Temperature affects chemical stability       |
| 4️⃣  | Optimal Charging Duration Class | 0.0016   | Minimal influence                            |

## 💬 Chatbot Integration

The chatbot extends the ML model into an interactive interface powered by **Groq's LLM API (Llama 3.3 70B)**, enabling natural language queries, feature extraction, and personalized explanations.

---

## 🔎 Solution Overview

- **Interactive Chatbot:** Groq LLM for natural conversations.  
- **ML Prediction Engine:** Random Forest + StandardScaler for degradation (%) forecasting from 4 inputs.  
- **Smart Feature Extraction:** Regex-based parsing of unstructured text.  
- **Dual-Path Logic:** Predict if data is complete; fallback to expert advice when needed.  
- **Secure Design:** Environment variables + modular Jupyter notebook architecture.

---

## 🛣️ Methodology & Workflow

1. **Input:** Natural query  
   _Example: "Charged EV 120 min at 80% SOC, 25°C battery"_

2. **Extraction:**  
   - Charging duration (min)  
   - SOC (%)  
   - Temperature (°C)  
   - Optimal class (inferred using logic)

3. **Prediction (if all features available):**  
   - Scale inputs → Random Forest → Degradation (%)

4. **Explanation:**  
   - Returned via Groq LLM  
   - _Example: "Expect ~2.5% degradation — tip: charge at lower SOC."_

5. **Fallback (missing data):**  
   - LLM acts as a general battery expert for guidance.

6. **Output:**  
   - Conversational, actionable health tips.

---

## ⚠️ Error Handling

- Fallback responses for:  
  - Missing or incomplete inputs  
  - API failures (e.g., model deprecation, parsing issues)  
- Secure API key management through **environment variables**.

---

## 🎓 Learning Objectives

- **EV Dynamics:** Modeled charging duration, temperature, and SOC for degradation prediction.  
- **NLP Basics:** Implemented regex + conditional rules for feature extraction.  
- **API Mastery:** Built a hybrid **ML + LLM** pipeline for seamless interaction.



## 🎯 Conclusion

The project successfully developed a *Machine Learning–powered EV Battery Degradation Prediction System, enabling accurate estimation of battery health using key operational parameters such as **charging duration, **State of Charge (SoC), and **thermal behavior*.

A *Random Forest Regression* model was trained after rigorous data preprocessing, achieving reliable prediction performance for battery degradation rate — helping support *preventive maintenance* and *extended battery lifespan*.

To enhance user interaction, an *intelligent Groq-based chatbot* was integrated, allowing users to input real-world battery conditions and receive *instant degradation predictions* along with clear, interpretable explanations.

The combined *ML model + LLM-powered chatbot* presents a practical, interactive, and scalable solution that can support *EV users, manufacturers, and service centers* in monitoring battery health more effectively.

This work demonstrates the potential of integrating traditional *Machine Learning* with state-of-the-art *Conversational AI, enabling more accessible, data-driven decision-making in the **electric mobility ecosystem**.

### 🛠️ Tech Stack

- **Language:** Python 🐍  
- **Libraries:**  
  - pandas  
  - numpy  
  - matplotlib  
  - seaborn  
  - scikit-learn  
- **Model Used:** Random Forest Regressor 🌲
- **LLM API:** Groq (Llama 3.3 70B) with groq-python SDK
- **Security:** Environment Variables (API Key)
- **Development Tools:**  
  - Jupyter Notebook  

### 🔐 API Key Setup
This project uses the Groq API for LLM access.

To test it yourself:
1. Create a free Groq account → [https://console.groq.com](https://console.groq.com)
2. Generate an API key.
3. Set it as a system environment variable:
   - **Windows (CMD):**
     ```bash
     setx GROQ_API_KEY "your_api_key_here"
     ```
   - **Mac/Linux:**
     ```bash
     export GROQ_API_KEY="your_api_key_here"
     ```
4. Restart Jupyter Notebook and run the chatbot.


## 👤 Author    
Chinta Harichandan    
📧 Email: harichandan130505@gmail.com  
🔗 LinkedIn Profile: https://www.linkedin.com/in/harichandan-chinta-210451346  
📂 GitHub: https://github.com/ChintaHariChandan  

## 📜 License
This project is licensed under the MIT License – feel free to use, modify, and distribute.
