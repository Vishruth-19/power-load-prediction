# Power System Load Type Prediction

## Project Overview
This repository contains a machine learning pipeline designed to predict the `Load_Type` (Light, Medium, or Maximum) of a power system based on historical continuous-time energy consumption data.

## Methodology
* Exploratory Data Analysis: Investigated the relationship between time of day (NSM) and energy usage (kWh) to identify distinct clustering based on load type.
* Feature Engineering: Extracted critical temporal features (Month, Day of Week, Hour, Weekend Boolean) to capture the cyclical nature of power consumption.
* Validation Strategy: Implemented a strict time-based split. To prevent data leakage and simulate real-world deployment, the model was trained on historical data and tested exclusively on the final chronologically sequenced month of data.
* Modeling: Utilized `XGBoost` for robust multi-class classification.

## Results
The model was evaluated on the unseen test set (the final month of data) achieving the following metrics:
* **Accuracy:** 0.8720
* **Precision:** 0.8952 (Weighted)
* **Recall:** 0.8720 (Weighted)
* **F1-Score:** 0.8753 (Weighted)

Key Insight: The model demonstrated exceptionally high recall for `Medium_Load` (0.95) and `Maximum_Load` (0.91). From a business and infrastructure perspective, this conservative prediction bias is ideal, as overestimating grid load is vastly preferable to underestimating peak demand.

## Files
* `main.ipynb`: The complete, runnable Jupyter Notebook containing EDA, preprocessing, and modeling.
* `load_data.csv`: The historical energy consumption dataset.