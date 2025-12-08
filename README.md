# 📈 Economic Trend Prediction Using Layoff Data & Stock Market Indicators  
### **Predicting S&P 500, Dow Jones, and VIX Daily Direction (2020–2023)**

This project builds a machine-learning pipeline to predict daily economic direction for major U.S. market indexes:

- **S&P 500 → SP5_Up**
- **Dow Jones → DJ_Up**
- **VIX Fear Index → VIX_Up**

The model uses combined datasets that include **company layoffs**, **stock index movements**, and **market sentiment indicators** to determine whether each index will go **Up (1)** or **Down (0)** on the next trading day.

---

## ⭐ 1. Project Overview
This project investigates whether layoffs and company-level stress signals can help predict short-term market movements.

### ✔ Data Sources
- Tech/company layoff events (industry, country, % laid off)
- S&P 500 daily close values
- Dow Jones Industrial Average daily close values
- VIX fear index values

### ✔ Outputs
- Market Up/Down predictions  
- Confusion matrices  
- Feature importance charts  
- Prediction vs Actual plots  
- Probability distribution graphs  

---

## 📊 2. Dataset Description

This project requires **four CSV files**, stored in the same directory as the script.

| File              | Description |
|-------------------|-------------|
| `layoffs.csv`     | Layoff events: company, industry, location, percentage laid off |
| `sp500.csv`       | Daily S&P500 closing values |
| `dow.csv`         | Daily Dow Jones values |
| `vix.csv`         | Daily VIX index levels |

All files are filtered to:  
**2020-03-11 → 2023-03-06**.

---

## 🛠️ 3. Data Cleaning & Preprocessing

### ✔ Date Range Filtering  
Keeps only rows between **March 2020 – March 2023**.

### ✔ Dataset Merging  
Merged on `Date` into a master dataset:


### ✔ Handling Missing Values  
Removes rows lacking `percentage_laid_off`.

---

## 🧩 4. Feature Engineering

### **A. Risk Category**
Generated based on percentage laid off:

| % Laid Off | Risk |
|------------|------|
| < 4%       | -1 (Low Risk) |
| 4–8%       | 1 (High Risk) |
| > 8%       | 3 (Extreme Risk) |

### **B. Layoff Index**
A custom categorical economic stress indicator.

### **C. Market Direction Labels**
- `SP5_Up = 1` if today’s S&P > yesterday  
- `DJ_Up = 1` if today’s Dow > yesterday  
- `VIX_Up = 1` if today’s VIX > yesterday  

These are the targets for model training.

### **D. Time-Based Features**
- `year`
- `month`
- `day`

Used for seasonality learning.

---

## 🤖 5. Machine Learning Model

### Model Used  
`DecisionTreeClassifier(max_depth=6)`

Chosen for:
- Mixed numerical + categorical data  
- Interpretability  
- Fast training  

### Preprocessing Pipeline

| Feature Type | Method |
|--------------|--------|
| Numerical    | Passthrough |
| Categorical  | OneHotEncoder(ignore_unknown="ignore") |

Implemented with **ColumnTransformer** + **Pipeline**.

---

## How to Run This Project

### Step 1 — Place all CSV files together
layoffs.csv
sp500.csv
dow.csv
vix.csv
### Step 2 — Run the script
open the jupyter notebook to run the final.ipynb
### Step 3 — View the outputs
Images and model results will be saved in your output directory.
### 8. Repository Structure
/Data
    layoffs.csv
    sp500.csv
    dow.csv
    vix.csv

/Notebooks
    EDA.ipynb
    Modeling.ipynb
    PredictionDemo.ipynb

/Model
    best_model.pkl

/Slides
    project_presentation

/summary
    summary


README.md
