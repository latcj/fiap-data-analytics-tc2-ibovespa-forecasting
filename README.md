# Tech Challenge 2 · Forecasting the Ibovespa closing index

How much does a model improve on repeating the last known close? This time-series project studies 2,729 Ibovespa trading sessions from January 2, 2015 through December 30, 2025. [Analysis notebook](notebooks/ibovespa.ipynb) · [Download the illustrated report](reports/ibovespa-forecasting.html?raw=1)

## Results

The three baselines started from the close on November 13, 2025 and forecast the same 30 trading sessions, from November 14 to December 30. Repeating the last close produced the lowest mean absolute percentage error (MAPE) among these three strategies.

| Baseline | Forecast rule | MAPE |
| --- | --- | ---: |
| Naive | Repeat the last observed close | 1.34% |
| Seasonal naive | Repeat the last five trading closes in order | 1.76% |
| Seasonal window average | Average the two most recent five-session cycles by position | 3.06% |

The notebook also fits ARIMA, Prophet and XGBoost. ARIMA uses the full history to select its orders. Prophet uses observed opening levels for the test period and compares calendar-day predictions with trading sessions by position. XGBoost’s **0.35% in-sample MAPE** includes next-session information in its features and uses the same rows for training and scoring. The five-weekday scenario illustrates how its estimates move when the opening level is held fixed.

## Reproduce the study

1. Place an authorized daily price export at `data/ibovespa.csv`. The data guide documents the English input format and the original provider format. [Data and units](data/README.md)
2. Use Python 3.12 in an activated virtual environment and run the commands below from the repository root.
3. In JupyterLab, choose **Run → Run All Cells**. This also recreates the price-history plots from the local input. The published report contains aggregate scores, diagnostics and the five-weekday scenario.

```shell
python -m pip install -r requirements.txt
python -m jupyterlab notebooks/ibovespa.ipynb
```

The study uses pandas, NumPy, Matplotlib, Seaborn, statsmodels, Prophet, XGBoost and scikit-learn.

Luiz Carvalho · FIAP postgraduate program in Data Analytics. [GitHub profile](https://github.com/latcj)
