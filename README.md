# International_Retail_Sales
# 📈 Retail Demand Forecasting: From Messy Data to Supply Chain Strategy

Hi there! Welcome to my Supply Chain Data Analytics project. 👋

If there's one thing I've learned about retail supply chains, it's that real-world sales don't follow the perfectly smooth, predictable curves we see in textbooks. They are volatile, influenced by macroeconomic factors, and heavily distorted by holiday spikes and promotional campaigns. 

I built this project to bridge the gap between theoretical Sales & Operations Planning (S&OP) and raw, chaotic retail data. The goal? To predict future demand accurately so a business can optimize inventory, prevent stockouts during peak seasons, and avoid tying up capital in overstock.

## 🤔 The Business Problem
Managing inventory across multiple stores and departments requires answering two critical S&OP questions:
1. **Micro-level (Short-term):** How much inventory do we need next week for specific departments, considering recent trends, holidays, and markdowns? 
2. **Macro-level (Long-term):** What does our capacity planning look like for the next 52 weeks?

## 🛠️ The Journey & The Methodology

Instead of just throwing a single algorithm at the dataset, I treated this as a full Data Science pipeline:

### 1. Macro-Level Exploratory Data Analysis (EDA)
At first, plotting every promotional markdown against weekly sales created a massive, unreadable cloud of noise (overplotting). To find the actual business insight, I aggregated the data to a **National Macro-Level**. This revealed a clear, measurable divergence: promotional budgets (MarkDowns) yield a significantly higher average ROI during holiday weeks compared to normal days. 

### 2. Time-Series Feature Engineering
Algorithms need "memory" to predict the future. I engineered features to help the models understand retail behavior:
* **Lags:** 1-week, 4-week, and 52-week (Year-over-Year) lags to capture recent momentum and annual cycles.
* **Rolling Means:** 4-week moving averages to smooth out weekly volatility.
* **Date Extraction & One-Hot Encoding:** Breaking down timestamps and treating holidays as distinct numeric flags.

### 3. The Model Showdown (Cross-Model Evaluation)
To ensure transparency and accountability in the forecasting model, I didn't rely on guesswork. I split the data chronologically (70% Train, 10% Validation, 20% Test) and ran a multi-model comparison:
* **Ridge Regression:** Used as a baseline. It failed to capture the non-linear complexity of retail sales.
* **LightGBM & XGBoost:** Powerful, but highly sensitive to random retail noise.
* **Random Forest (The Winner):** Thanks to its bagging mechanism, it successfully filtered out the outliers and noise, achieving the lowest MAE and RMSE for short-term, micro-level forecasting.
* **Facebook Prophet:** Deployed separately to handle 52-week long-term capacity planning due to its excellent decomposition of seasonality and holiday impacts.

## 💻 Tech Stack
* **Language:** Python (Jupyter Notebook)
* **Data Processing & EDA:** `pandas`, `numpy`, `matplotlib`, `seaborn`
* **Machine Learning:** `scikit-learn` (Random Forest, Ridge), `xgboost`, `lightgbm`, `prophet`
