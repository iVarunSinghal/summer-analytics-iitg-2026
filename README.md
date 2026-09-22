# GreenTravel Intelligence Challenge - Part B Submission
**Author:** Varun Singhal, IIT Guwahati

## 📁 Contents
* **`notebooks/GreenTravelHighCarbonPrediction.ipynb`**: Full, executed notebook (EDA, feature engineering, model comparison, evaluation, leakage-check ablation, and final private-set prediction). All cells already contain their output from a real run.
* **`submissions/submission.csv`**: Final predictions (TripID, HighCarbon probability) for the 21,764 private trips.

## ⚙️ To reproduce from scratch:
1. Place all 6 challenge CSVs (`public_trip_data.csv`, `public_trip_event_log.csv`, etc.) in the `data/raw/` folder.
2. Open the notebook in Jupyter and Run All. *(If the CSVs are in a different folder, edit the `DATA_DIR` variable in the second code cell.)*
3. This regenerates `submission.csv` identically.

## 📊 Results summary:
* **Model:** XGBoost (selected over LightGBM via 5-fold CV: 0.9993 vs 0.9992)
* **Holdout ROC-AUC:** 0.9994 | **F1:** 0.987 | **Precision:** 0.989 | **Recall:** 0.985
* **Leakage check (ablation):** `route+mode` features alone achieve 0.997 ROC-AUC, confirming the model's strength comes from legitimate, permitted signal (distance x mode-specific emission factor) rather than any leakage.
