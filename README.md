# Economic-Predictions-By-Layoffs
1. Problem Statement
The goal of this project is to predict daily financial market movements, specifically whether the S&P 500 (SP5_Up), Dow Jones (DJ_Up), or VIX volatility index (VIX_Up) will increase based on layoffs and company-level attributes. This explores whether layoff activity, industry, geographic location, and timing provide predictive signals for short-term market direction.
2. Data
The dataset combines four sources:
• Global Layoff Dataset (company, industry, location, stage, layoffs %, country)
• S&P 500 daily prices (SP5)
• Dow Jones daily prices (DJIA)
• VIX (Volatility Index)
Binary targets:
• SP5_Up = 1 if today’s S&P 500 > yesterday  
• DJ_Up = 1 if Dow Jones > yesterday  
• VIX_Up = 1 if VIX increased  
3. Model
A Decision Tree Classifier was selected because it handles mixed data types and provides interpretability.
Pipeline included:
• ColumnTransformer (numeric passthrough + OneHotEncoder)  
• DecisionTreeClassifier(max_depth=6)  
Train-test split: 80/20  
Separate models were trained for SP5_Up, DJ_Up, and VIX_Up.
4. Results
SP5_Up:
• Accuracy: 0.8762  
• Top features: Month, Year, Finance/Travel industries, locations (Seattle, SF Bay Area)
VIX_Up:
• Accuracy: 0.8889  
