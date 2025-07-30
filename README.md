# Blockhouse-Assignment
# Algorithmic Execution: Price Impact Modeling & Optimization

This repository contains the solution for the Blockhouse Work Trial Task. The project involves a deep dive into high-frequency limit order book data to model temporary price impact and formulate a risk-averse optimal execution strategy.

---

## 📝 Problem Statement

The assignment consists of two main tasks:
1.  **Model the temporary price impact function `g_t(x)`**. This involves analyzing order book data for three tickers (FROG, CRWV, SOUN) to propose and justify a model superior to a simple linear approximation.
2.  **Formulate a mathematical framework for an optimal execution algorithm**. This algorithm should aim to execute a large order `S` over `N` periods while minimizing execution costs.

---

## 🔬 Methodology

A multi-model comparative framework was employed to find the most effective impact model.
* **Empirical Ground Truth:** The true, piecewise impact function was calculated by simulating trades against the raw order book data.
* **Square-Root Model:** The industry-standard `g_t(x) = C_t * sqrt(x)` model was fitted to the empirical data for each minute of the trading day.
* **Machine Learning Model:** A Random Forest Regressor was used as a benchmark to test the limits of predictive accuracy.

The final execution strategy was formulated using principles from the **Almgren-Chriss** model, solved via **Dynamic Programming**.

---

## 📊 Key Findings

* The **Square-Root model** provides an excellent balance of accuracy and interpretability, successfully capturing the concave nature of price impact.
* The impact parameter **`C_t` varies significantly** across different stocks and throughout the trading day, often exhibiting a U-shaped pattern (higher impact at market open/close).
* The proposed execution framework uses the time-varying `C_t` to intelligently schedule trades, balancing the costs of market impact and price risk.

---
## 💿 Data

To ensure the analysis is reproducible, the data file for one of the three tickers, **FROG**, has been included in the `/data` folder.
The other two data files (**CRWV** and **SOUN**) were excluded from this repository as they exceed GitHub's 25 MB file size limit. All three original data files were provided as part of the work trial and are from **Databento**.

## 🚀 How to Run

1.  **Environment:** This project is designed to run in a Python environment like Google Colab.
2.  **Data:** Upload the provided data CSV files (`FROG...`, `CRWV...`, `SOUN...`) to the root directory.
3.  **Execution:** Run the `.ipynb` notebook. The notebook is self-contained and will perform the full analysis, generating the comparative plots and statistics.
