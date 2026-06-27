## Conformal Inventory Optimization (M5 Hackathon)

An end-to-end machine learning pipeline built to crush uncalibrated uncertainty in high-volume retail supply chains. By wrapping parallel LightGBM quantile regressors with **Split Conformal Prediction**, this framework mathematically nears a $95\%$ statistical coverage shield while slicing logistics operations costs by **$62.2\%$**.

---

##  Repository Structure & Navigation

The codebase and matching output logs are bundled into three distinct pipeline stages. Unzip them in order to explore or run the assets:

* **`stage1_preprocess.zip`**
    * `pre_process.py`: Ingests raw M5 CSVs, downcasts datatypes to maximize memory efficiency, and exports clean chronological **1500 / 400 / 41 day data splits** into compressed Parquet frames for **training, caliberation and testing**.
    * *Telemetry:* Prints live data samples to track layout variations and downcast confirmations step-by-step.

* **`stage2_training.zip`**
    * `generate_predictions.py`: Fits the dual-core LightGBM models (Mean point baseline, $5^{\text{th}}$, and $95^{\text{th}}$ asymmetric quantiles) and computes the conformal correction factor ($Q_{1-\alpha}$). Partitions absolute widths into balanced **Low, Moderate, and High Risk Tiers** using width quantiles.
    * `test_forecasting_results.csv`: Master prediction database mapped which predicts daily sales of the products, includes **point estimates**, **quantile intervals**, **conformal bounds** and **risk tier**.

* **`stage3_simulation.zip`**
    * `inventory_simulation.py`: Runs a post-prediction financial logistics case study, testing the uncertainty-aware conformal policy against a naive point baseline using standard retail holding costs ($0.10) vs stockout penalty fees ($2.00).
    * `empirical_calibration_curve.png`: High-resolution scatter plot tracking nominal confidence targets against true observed empirical coverage coordinates.
    * `volatility_underestimation_report.csv` & `final_inventory_simulation_scorecard.csv`: Audits the statistical system to prove a massive $62.2\%$ total operational cost-optimization savings.

---

##  Core Metrics 
* **The Bottom Line:** Slashed total supply chain operational costs from **$20.57M** (naive point policy) to **$7.77M** (uncertainty-aware conformal policy).
* **Stockout Protection:** Dropped lost product units from **9.99M** units down to **1.91M** units by providing a robust volatility shield over chaotic demand slices.
* **Model Comparison:** While pure quantile regression builds uncalibrated retail intervals that collapse and underestimate risk during chaotic holiday rushes, conformal prediction acts as a vital reality check by mathematically stretching those safety ranges to guarantee an honest $95\%$ accuracy shield on the store floor.
* **True 95% Calibration:** Closes the overconfidence gap of standalone ML models, boosting real-world coverage to **$93.33\%$ overall** ($93.78\%$ in high-volatility windows).



