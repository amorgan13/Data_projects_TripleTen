# Churn Model Deliverable

Contents:
- model_artifacts/
  - final_pipeline.joblib  (pipeline: preprocessor + classifier)
  - model_manifest.json    (feature list, thresholds, CV summary)
  - preprocessor_manifest.json (preprocessing rules and derived feature formulas)
  - chosen_threshold.json
- figures/
  - permutation_importance_reduced_top25.png
  - roc_curve_validation.png
  - pr_curve_validation.png
  - confusion_best_f1.png (if present)
- appendix/
  - permutation_importance_reduced.csv
  - threshold_metrics_validation.csv
  - merged_clean_fe.csv (or FE reproduction script)
- README.txt (this file)

Quick usage:
```python
import joblib, json, pandas as pd
pipe = joblib.load("model_artifacts/final_pipeline.joblib")
mm = json.load(open("model_artifacts/model_manifest.json"))
features = mm["features"]
th = json.load(open("model_artifacts/chosen_threshold.json"))["best_f1_threshold"]
df_new = pd.read_csv("appendix/merged_clean_fe.csv")
probs = pipe.predict_proba(df_new[features])[:,1]
preds = (probs >= th).astype(int)
```

```python
import joblib, json, pandas as pd  
pipe = joblib.load("data/processed/final_pipeline.joblib")  
th = json.load(open("data/processed/chosen_threshold.json"))["best_f1_threshold"]  
mm = json.load(open("data/processed/model_manifest.json"))
features = mm["features"]  
df_new = pd.read_csv("path_to_new_FE_table.csv")  
