# Forecasting ride-hailing demand in space and time (Tallinn)

Take-home exercise for a (Senior) Data Scientist application at a ride-hailing company (2023).

The task was to use ~630,000 rows of synthetic ride-request data for Tallinn (pick-up time, pick-up and drop-off coordinates, ride value) to suggest a way of guiding drivers towards areas with higher expected demand, build and document a baseline model, and describe deployment, driver communication, and the design of a live experiment.

**View the rendered notebook:** download `rideshare_demand.html` and open it in a browser (the interactive maps do not render in GitHub's notebook preview).

## Contents

- `rideshare_demand.ipynb`: the notebook, with outputs
- `rideshare_demand.html`: rendered version of the notebook, including interactive heat maps

## Approach

1. Exploratory analysis of the spatial and temporal structure of ride demand, including interactive heat maps (folium)
2. Enrichment with hourly historical weather data (Weatherstack API)
3. Aggregation into H3 hexagonal cells × one-hour time slots
4. Comparison of regularized linear regression (Lasso) and XGBoost regression, with time-series cross-validation and stepwise hyperparameter tuning
5. Notes on deployment, communicating recommendations to drivers, and experiment design

## Reproducing

The dataset is not included in this repository. Re-running the notebook requires the data at `data/robotex5.csv`, a `models/` directory, and a Weatherstack API key in the `WEATHERSTACK_API_KEY` environment variable. The code was written in 2023 against older library versions (e.g., `h3` 3.x, pandas 1.x, scikit-learn < 1.6); see `requirements.txt`.
