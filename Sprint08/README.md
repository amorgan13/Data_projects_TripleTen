# Customer Churn Prediction: Evaluation and Predictions

## 🏆 Introduction
Beta Bank is facing a **customer churn problem** that can be addressed through **research and machine learning**. Using a dataset of **10,000 customers**, I built a model to **predict which clients are at risk of leaving the bank**. The goal was to determine the most effective model for accurate churn prediction.

---

## 🔬 Pre-Processing Methods
To prepare the data for machine learning, I performed several **pre-processing steps**:
1. **Removed irrelevant columns** to streamline model training.
2. **Converted categorical data to numerical values** using **One-Hot Encoding**.
3. **Split the dataset** into **training, validation, and test sets**.
4. **Scaled the numerical data** to normalize feature distributions.

These steps ensured the data was properly formatted and optimized for machine learning models.

---

## 📊 Balancing Methods
Since the dataset had an **imbalance in churned vs. non-churned clients**, I tested two methods to improve model performance:
1. **Upsampling** - Increased the number of churn observations to balance the dataset.
2. **Class Weight Parameter** - Adjusted model weights to give higher importance to the underrepresented class.

**Findings:** The **upsampling method** produced higher **F1 scores**, suggesting it was the more effective approach for predicting churn.

---

## 🎯 Models Used
I trained and compared the performance of **three classification models**:
1. **Logistic Regression: "class_weight=balanced**
2. **Logistic Regression: with Random Undersampling**
3. **Random Forest: with Random Upsampling**

Each model's performance was evaluated based on the **F1 score**, a balance between precision and recall.

---

## 🔍 Findings and Conclusion
The **Random Forest model: with Random Upsampling** achieved the highest **F1 score**, making it the most effective choice for predicting customer churn.

### **F1 Scores:**
- **Logistic Regression: "class_weight=balanced** = **0.435**
- **Logistic Regression: with Random Undersampling** = **0.433**
- **Random Forest: with Random Upsampling** = **0.635**

Since the **Random Forest model** provided the best balance of precision and recall, **Beta Bank should use this model** to identify at-risk clients.

🚀 **Future Work:** Exploring alternative feature engineering techniques, testing additional models, and optimizing hyperparameters may further improve churn predictions.

