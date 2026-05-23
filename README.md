# 📈 AdEase – Wikipedia Page Views Time Series Forecasting

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Jupyter](https://img.shields.io/badge/Made%20with-Jupyter-orange.svg)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen.svg)
![License](https://img.shields.io/badge/License-Educational-lightgrey.svg)

> Forecasting daily Wikipedia page views for the next **60 days** using **ARIMA**, **SARIMAX**, and **Facebook Prophet** — built as a real-world style assignment for **AdEase**, a digital advertising company.

---

## 🧠Project Overview

**AdEase** helps clients place ads on the most relevant web pages so they reach the right audience at the right time. To do this effectively, AdEase needs reliable forecasts of **Wikipedia page traffic** across different languages and access types.

This project builds end-to-end time series models that capture:
- 📊 **Trend** — long-term direction of page views
- 🔁 **Seasonality** — weekly and yearly cycles
- 🌍 **Language-specific patterns** — behavior across regions
- 📢 **Campaign effects** — impact of marketing pushes (via SARIMAX)

---

## 🎯 Problem Statement

> Forecast Wikipedia page views for the **next 2 months (60 days)** so AdEase can optimize **ad placement** and **pricing** across multiple languages and access types.

---

## 📂 Dataset

| File | Description |
|------|-------------|
| `train_1.csv` | Daily page views from **2015-07-01 → 2016-12-31** for ~**145,000** Wikipedia articles |
| `Exog_Campaign_eng.csv` | Binary indicator of active marketing campaigns on English pages (exogenous variable for SARIMAX) |

Each article title encodes metadata: **page name**, **language**, **access type** (desktop / mobile-web / all-access), and **agent** (spider / user / all-agents).

---

## 🛠️ Approach

### 1️⃣ Exploratory Data Analysis (EDA)
- Inspected missing values, view distributions, and overall trends
- Aggregated views by language to compare regional behavior

### 2️⃣ Preprocessing
- Parsed metadata (language, access type, agent) from article titles
- Handled missing values and resampled into clean daily series

### 3️⃣ Stationarity Checks
- Applied **Augmented Dickey-Fuller (ADF)** test
- Used rolling statistics and differencing where needed

### 4️⃣ Decomposition
- Broke the series into **trend**, **seasonal**, and **residual** components

### 5️⃣ Modeling

| Model | Description |
|-------|-------------|
| 🟦 **ARIMA** | Baseline univariate model tuned with ACF/PACF and grid search on (p, d, q) |
| 🟩 **SARIMAX** | Seasonal ARIMA using the campaign indicator as an exogenous regressor |
| 🟧 **Facebook Prophet** | Additive model with trend, weekly/yearly seasonality, and holiday effects |

### 6️⃣ Evaluation
- Compared models using **MAPE** and **RMSE** on a held-out validation window
- Generated **60-day forecasts with confidence intervals** for the chosen model

---

## 📁 Repository Structure

```
adease-wikipedia-timeseries-forecasting/
│
├── AdEase_Time_Series.ipynb   # End-to-end notebook (EDA → modeling → forecasting)
└── README.md
```

---

## 🚀 How to Run

### Option 1 — Google Colab (Recommended ✅)
1. Open `AdEase_Time_Series.ipynb` in this repo
2. Click the **Open in Colab** badge at the top of the notebook
3. Upload `train_1.csv` and `Exog_Campaign_eng.csv` when prompted (or mount Google Drive)
4. Run all cells top-to-bottom ▶️

### Option 2 — Local Environment 💻

```bash
# Clone the repo
git clone https://github.com/MateenahJAHAN/adease-wikipedia-timeseries-forecasting.git
cd adease-wikipedia-timeseries-forecasting

# Create a virtual environment
python -m venv .venv
source .venv/bin/activate          # On Windows: .venv\Scripts\activate

# Install dependencies
pip install numpy pandas matplotlib seaborn statsmodels pmdarima prophet jupyter

# Launch the notebook
jupyter notebook AdEase_Time_Series.ipynb
```

---

## 📚 Key Libraries

| Library | Purpose |
|---------|---------|
| `pandas`, `numpy` | Data manipulation |
| `matplotlib`, `seaborn` | Visualization |
| `statsmodels` | ADF test, ARIMA, SARIMAX, seasonal decomposition |
| `pmdarima` | Auto-ARIMA for hyperparameter tuning |
| `prophet` | Facebook Prophet forecasting |

---

## 📊 Results

The notebook reports **MAPE** and **RMSE** for ARIMA, SARIMAX, and Prophet on the validation horizon, along with **60-day forecasts** featuring uncertainty bands.

👉 See the **final cells** of the notebook for:
- 📈 Forecast plots
- 📋 Model comparison table
- 🔍 Insights and conclusions

---

## 👩‍💻 Author

**Mateenah Jahan**  
🔗 GitHub: [@MateenahJAHAN](https://github.com/MateenahJAHAN)

---

## 📜 License

This project is shared for **educational and portfolio** purposes.

---

⭐ *If you found this project helpful or interesting, consider giving it a star!*
