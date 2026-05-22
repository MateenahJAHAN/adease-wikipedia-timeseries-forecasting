> **Author:** Mateenah Jahan — [@MateenahJAHAN](https://github.com/MateenahJAHAN)

# AdEase – Wikipedia Time Series Forecasting

Time series forecasting of Wikipedia page views using **ARIMA**, **SARIMAX**, and **Facebook Prophet**. This is an assignment project completed for **AdEase**, a digital advertising company that helps clients place ads on relevant pages so they reach the right audience.

## Problem Statement

AdEase wants to forecast the **views on different Wikipedia pages** for the next **2 months (60 days)** so that they can effectively manage ad placement and pricing for their clients. The pages span multiple languages and access types, and the goal is to build models that capture the trend, seasonality, and language-specific patterns in page views.

## Dataset

- **train_1.csv** – contains daily page views from `2015-07-01` to `2016-12-31` for ~145k Wikipedia articles.
- - **Exog_Campaign_eng.csv** – binary exogenous variable indicating days on which a marketing campaign was active for English pages (used in SARIMAX).
 
  - Each row corresponds to one Wikipedia article. The article name encodes the **page name**, **language**, **access type** (desktop / mobile-web / all-access), and **agent** (spider / user / all-agents).
 
  - ## Approach
 
  - 1. **Exploratory Data Analysis (EDA)**
    2.    - Inspected missing values, distribution of views, and overall trends.
          -    - Aggregated views by language to compare behavior across regions.
               - 2. **Preprocessing**
                 3.    - Parsed page metadata (language, access type, agent) from article titles.
                       -    - Handled missing values and resampled data into a clean daily time series.
                            - 3. **Stationarity Checks**
                              4.    - Used the **Augmented Dickey-Fuller (ADF)** test and rolling statistics to assess stationarity.
                                    -    - Applied differencing where required.
                                         - 4. **Decomposition**
                                           5.    - Decomposed the series into trend, seasonal, and residual components to understand the underlying structure.
                                                 - 5. **Modeling**
                                                   6.    - **ARIMA** – baseline univariate model tuned via ACF/PACF and grid search on `(p, d, q)`.
                                                         -    - **SARIMAX** – seasonal ARIMA with the campaign indicator as an exogenous regressor.
                                                              -    - **Facebook Prophet** – additive model capturing trend, weekly/yearly seasonality, and holiday effects.
                                                                   - 6. **Evaluation**
                                                                     7.    - Compared models using **MAPE** / **RMSE** on a held-out validation window.
                                                                           -    - Generated 60-day forecasts with confidence intervals for the chosen model.
                                                                            
                                                                                - ## Repository Structure
                                                                            
                                                                                - ```
                                                                                  adease-wikipedia-timeseries-forecasting/
                                                                                  ├── AdEase_Time_Series.ipynb   # End-to-end notebook (EDA, modeling, forecasting)
                                                                                  └── README.md
                                                                                  ```

                                                                                  ## How to Run

                                                                                  ### Option 1 – Google Colab (recommended)

                                                                                  Open the notebook directly in Colab and run the cells top-to-bottom:

                                                                                  1. Click `AdEase_Time_Series.ipynb` in this repo.
                                                                                  2. 2. Click the **Open in Colab** badge at the top of the notebook.
                                                                                     3. 3. Upload `train_1.csv` and `Exog_Campaign_eng.csv` when prompted (or mount Google Drive).
                                                                                       
                                                                                        4. ### Option 2 – Local environment
                                                                                       
                                                                                        5. ```bash
                                                                                           git clone https://github.com/MateenahJAHAN/adease-wikipedia-timeseries-forecasting.git
                                                                                           cd adease-wikipedia-timeseries-forecasting

                                                                                           python -m venv .venv
                                                                                           source .venv/bin/activate   # on Windows: .venv\Scripts\activate

                                                                                           pip install numpy pandas matplotlib seaborn statsmodels pmdarima prophet jupyter
                                                                                           jupyter notebook AdEase_Time_Series.ipynb
                                                                                           ```

                                                                                           ## Key Libraries

                                                                                           - `pandas`, `numpy` – data manipulation
                                                                                           - - `matplotlib`, `seaborn` – visualization
                                                                                             - - `statsmodels` – ADF test, ARIMA, SARIMAX, seasonal decomposition
                                                                                               - - `pmdarima` – auto-ARIMA for hyperparameter search
                                                                                                 - - `prophet` – Facebook Prophet forecasting
                                                                                                  
                                                                                                   - ## Results
                                                                                                  
                                                                                                   - The notebook reports forecast accuracy (MAPE/RMSE) for ARIMA, SARIMAX, and Prophet on the validation horizon and presents 60-day forecasts with uncertainty bands. See the final cells of the notebook for plots and the comparison table.
                                                                                                  
                                                                                                   - ## Author
                                                                                                  
                                                                                                   - **Mateenah Jahan** – [@MateenahJAHAN](https://github.com/MateenahJAHAN)
                                                                                                  
                                                                                                   - ## License
                                                                                                  
                                                                                                   - This project is shared for educational and portfolio purposes.
                                                                                                   - 
