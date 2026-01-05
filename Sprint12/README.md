# Used Car Value Prediction: Evaluation and Predictions

## 🏆 Introduction
Rusty Bargain requested a quality model to **predict the value of used cars** efficiently while ensuring **fast training and prediction times**. The goal of this project was to develop an accurate, yet computationally efficient, predictive model for used car pricing.

---

## 🔬 Process
I conducted **Exploratory Data Analysis (EDA)** on the provided `car_data.csv` file to clean and prepare it for machine learning. The dataset contained unnecessary columns, which were removed to streamline the model-building process. Additionally, I engineered key features such as **vehicle age** and **listing duration** to improve model performance. Data with inconsistent or incorrect values was also filtered out.

Once the dataset was prepared, I split it into **training (75%) and testing (25%)** sets. Then, I compared the performance of seven different machine learning regression models:
1. **Decision Tree**
2. **Random Forest**
3. **Linear Regression**
4. **Gradient Boosting**
5. **XGBoost**

The goal was to find the model with the **lowest RMSE** while also considering training and prediction speed. The **XGBoost model** proved to be the most efficient.

### Model Quality
The table below summarizes the performance of each model based on several metrics (MAE, RMSE, R²) on both the log-transformed and original price scales:

| Model              | Log MAE | Log RMSE | Log R²  | MAE    | RMSE   | R²      |
|--------------------|---------|----------|---------|--------|--------|---------|
| Linear Regression  | 0.524   | 0.776    | 0.555   | 2265   | 30484  | -42.95  |
| Decision Tree      | 0.394   | 0.634    | 0.703   | 1354   | 2154   | 0.78    |
| Random Forest      | 0.374   | 0.606    | 0.728   | 1281   | 2054   | 0.80    |
| Gradient Boosting  | 0.347   | 0.575    | 0.755   | 1163   | 1894   | 0.83    |
| XGBoost            | 0.347   | 0.575    | 0.755   | 1160   | 1889   | 0.83    |

- **Best Model(s):** Both Gradient Boosting and XGBoost achieved the best results, with the lowest MAE/RMSE and highest R² (≈0.83) on the original price scale.
- **Linear Regression** performed much worse, with a negative R² on the original scale, indicating it is not suitable for this problem.
- **Random Forest and Decision Tree** performed better than Linear Regression, but were still outperformed by gradient boosting methods.

### Model Speed

- **Linear Regression** was the fastest to train and predict (almost instantaneous).
- **Decision Tree** was also very fast, though a bit slower than Linear Regression.
- **Random Forest, Gradient Boosting, and XGBoost** took noticeably longer to train, especially on a large dataset. Among these, **XGBoost** and **Gradient Boosting** were the slowest, but the difference in speed is justified by their superior accuracy.
- For most real-world applications, the extra training time of ensemble methods is acceptable given their much better performance.

---

## 📊 Conclusion
I recommend that **Rusty Bargain** use the **XGBoost** model for predicting used car values. This model provides the best balance between **accuracy and efficiency**, making it ideal for real-time application needs.

🚀 **Future Work:** Further integrating additional feature engineering techniques, and exploring ensemble methods could enhance predictive performance even more.

