# Sprint 17: Customer Churn Prediction

## 🏆 Introduction
Interconnect tasked me with creating a **predictive model** to identify customers most likely to **cancel their services**. The goal was to analyze customer data, handle class imbalance, and implement machine learning models to accurately predict churn.

---

## 🔬 Process
### Data Preparation
Interconnect provided **four different CSV files**, which required extensive **cleaning and merging**. The dataset included **begin and end date columns**, allowing me to calculate **contract length** and **churn status**. Customers **without an end date** were considered **active users**. After processing, the dataset contained **7,000 observations**, with **26.5% representing churned customers**.

### Feature Engineering & Encoding
Most of the dataset contained **categorical variables**, requiring **One-Hot Encoding** to convert them into numerical format for machine learning models.

---

## 📊 Model Comparisons
I implemented three different machine learning models and evaluated their **AUC-ROC scores**:

1. **Random Forest Classifier**: Achieved an AUC-ROC score of **0.89**. This model showed strong predictive power but was outperformed by others.
2. **Logistic Regression**: Performed the worst, achieving an AUC-ROC score of **0.87**. Due to its lower predictive accuracy, this model is **not recommended**.
3. **LightGBM (Gradient Boosting)**: **Top performer** with an AUC-ROC score of **0.93**. This model was not only accurate but also computationally efficient.

---

## ✅ Conclusion & Recommendations
### 🔹 Best Model: **LightGBM**
Based on performance metrics, I recommend **Interconnect use the LightGBM model** for predicting customer churn. This model offers **high accuracy (AUC-ROC: 0.93)** and is computationally **efficient for large datasets**.

### 🔹 Key Insights
- **Most important churn indicators (LightGBM model)**:
  - **Contract Length**
  - **Monthly Charges**
  - **Total Charges**
- **Random Forest model insights**:
  - Additional factors such as **Fiber Optic Services** and **Total Charges** were important predictors of churn.

### 🔹 Next Steps for Interconnect
- **Investigate customer concerns** related to **contract length, pricing models, and payment methods**.
- **Optimize service offerings** for customers in high-risk churn categories.
- **Monitor and improve billing processes**, especially for **electronic check users**.

🚀 **Future Work:** Additional hyperparameter tuning and testing alternative ensemble models could further improve predictive accuracy.

