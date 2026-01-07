Title: Churn Prediction — Model Development, Evaluation, and Artifacts

Author: [Alexis Tennis]
Date: [11/06/2025]

This report describes the development of a customer churn prediction model using feature engineering, model comparison, targeted feature selection, and validation. I compared logistic regression, Random Forest, and LightGBM using stratified cross-validation and selected a reduced LightGBM model for deployment. SHAP was attempted as planned but blocked by the execution environment; instead I used permutation importance and built-in tree importances to explain model behavior.

1. Data and Preprocessing
- Data used: final feature-engineered table saved at data/processed/merged_clean_fe.csv.
- Missingness and sentinel rules: categorical missing values were imputed with "##NA##", binary missing values imputed to 0, numeric missing values imputed with median (details and exact sentinel values in data/processed/preprocessor_manifest.json).
- Derived features: see preprocessor_manifest.json for formulas. Key derived features used in the final model include:
  - TotalCharges_log1p_capped = log1p(min(TotalCharges, cap_value))
  - TotalCharges_capped = min(TotalCharges, cap_value)
  - TotalCharges_log1p = log1p(TotalCharges)
  - (If used) avg_monthly_from_total = TotalCharges / tenure_months_snapshot when tenure>0 else MonthlyCharges

2. Feature Engineering Stage 
- Finalized service flags, tenure bins, payment/contract one-hot encodings, and missingness indicators.
- Created candidate ratio features and tested them with quick Random Forest probes (none produced persistent gains beyond the final reduced set).
- Used permutation importance and a small ablation procedure to prune low-importance features.

3. Model comparison and selection
- Models compared (5-fold stratified CV, ROC AUC):
  - Logistic regression: ROC AUC mean ≈ 0.8703
  - RandomForest: ROC AUC mean ≈ 0.8934
  - LightGBM: ROC AUC mean ≈ 0.9364 (selected)
- The model_comparison_results.json file contains full CV summaries and per-fold metrics.

4. Feature selection and final model
- Using permutation importance, I selected the top-10 features (reduced_features.json) and re-fit LightGBM on full data with that set.
- The reduced feature list (saved in model_manifest.json and reduced_features.json):
  1. TotalCharges_log1p_capped
  2. tenure_months_snapshot
  3. MonthlyCharges
  4. TotalCharges_capped
  5. Type
  6. InternetService
  7. TotalCharges_log1p
  8. PaymentMethod
  9. StreamingMovies_bin
  10. MultipleLines_bin

5. Explainability (SHAP attempt blocked)
- Planned: SHAP for local and global explanations.
- Execution: attempted to install SHAP in the execution environment, but installation was blocked by system (Attempted everything I could think of, even tried every idea Dot gave me, but was still unsuccessful.) As alternatives I produced:
  - Permutation importance (global, model-agnostic): data/processed/permutation_importance_reduced.csv
  - Tree feature importances (where applicable)
  - Logistic regression coefficients for baseline (for directionality)
- Permutation importance plot is saved at data/processed/permutation_importance_reduced_top25.png.

6. Validation, threshold selection, and deployment artifacts
- Validation (held-out 20% stratified split) results:
  - Validation ROC AUC: 0.9400 (final reduced model)
  - Candidate thresholds (saved in data/processed/chosen_threshold.json):
    - best_f1_threshold ≈ 0.66 (precision ≈ 0.867, recall ≈ 0.749, F1 ≈ 0.803)
    - best_j_threshold ≈ 0.40  (higher recall ≈ 0.853, precision ≈ 0.727)
  - Threshold metrics and confusion matrices: data/processed/threshold_metrics_validation.csv
  - ROC and PR curves: data/processed/roc_curve_validation.png and data/processed/pr_curve_validation.png

7. Limitations and notes
- SHAP analyses were part of the original plan but could not be executed due to package installation restrictions in the execution environment. The report includes alternative explainability outputs (permutation importance, tree importances, logistic coefficients).
- The reduced feature set produced better validation performance in this workflow, but alternative feature engineering (target encoding, additional interactions) might yield further gains if permitted.

