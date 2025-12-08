#Economic Trend Prediction Using Layoff Data + Stock Market Indicators
#Predicting SP500, Dow Jones, and VIX Daily Direction Using Machine Learning (2020–2023)
#1. Project Overview
This project builds a machine-learning system that predicts daily economic direction:
SP500 Up / Down
Dow Jones Up / Down
VIX Index Up / Down
using combined datasets of:
U.S. layoff events (company, industry, location, % laid off)
S&P500 historical values
Dow Jones Industrial Average
VIX fear index
The goal is to explore whether tech layoffs and company-level economic stress signals can predict short-term market movements.
#2. Dataset Description
This project requires four CSV inputs (10 years each, filtered to 2020–2023):
Dataset	Description
layoffs.csv	Company layoff events: percentage laid off, industry, location, etc.
s_p.csv / sp500.csv	Daily S&P500 closing values
dow.csv	Daily Dow Jones index values
vix.csv	Daily VIX index (fear index)
All files must be stored in the same folder as the main script.
#3. Data Cleaning & Preprocessing
The script performs:
✔ Date filtering
Only keeps data between 2020-03-11 → 2023-03-06, matching the availability of layoff reports.
✔ Merging data
All datasets are merged into one master table on the Date field:
LAYOFFS + SP500 + DOW + VIX
✔ Missing data removal
Rows without percentage_laid_off are removed.
✔ Feature engineering
Four new features are created:
A. Risk Category (Target for analysis)
-1 → Low Risk (< 4%)
 1 → High Risk (4–8%)
 3 → Extreme Risk (> 8%)
B. Layoff Index (Custom Categorical Signal)
Used by the ML model.
C. Economic direction labels
SP5_Up = 1 if today's SP500 > yesterday
DJ_Up  = 1 if today's Dow > yesterday
VIX_Up = 1 if today's VIX > yesterday
D. Time signals
year, month, day
These help the model learn seasonal patterns.
4. Machine Learning Model
The project uses:
DecisionTreeClassifier (max_depth=6)
This model performs well on mixed numerical and categorical datasets.
Preprocessing Pipeline
Numerical features → passthrough
Categorical features → One-Hot Encoding
Using ColumnTransformer ensures clean, consistent preprocessing.
5. Training Function
The function:
train_and_plot(df, target_name)
trains a model for any target:
SP5_Up
DJ_Up
VIX_Up
It automatically generates:
✔ Accuracy score
✔ Confusion matrix PNG
✔ Feature importance chart PNG
✔ Prediction vs Actual plot
✔ Probability distribution plot

# Remember to setup your own output file path to save all images
How to Run the Project
Step 1 — Place all CSV files in the same folder as your Python script
Step 2 — Run the script
