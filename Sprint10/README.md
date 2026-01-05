# Gold Recovery Process: Evaluation and Predictions

## 🏆 Introduction
Zyfra is looking to create a predictive model that will help a gold mining and refinement company develop more efficient processes. In this project, I explore the provided data in three datasets to ensure its usability for machine learning. I then prepare it for analysis. Once the data is fully ready, I use three different regression models to find optimized solutions for the gold mining company.

---

## 🔬 Process
I developed a machine learning pipeline to predict gold recovery at two key stages in the flotation process: rougher and final recovery. The workflow encompassed thorough data preprocessing, feature selection, model training, and rigorous evaluation using cross-validation and the sMAPE metric.

The data came in three different files: **Training, Test, and Full**. The Test set did not include all the columns that the Training and Full sets did. To address this, I used the **Date** column as a functional ID for each observation and matched the corresponding dates from the Full set to extract the missing columns. Once I had a complete dataset, I cleaned the data and verified that the calculated columns were correctly computed.

After the data was cleaned, I wrote a function to calculate the **sMAPE score** for each prediction. Then, I used the training dataset to build two machine learning regression models:
1. **Random Forest**
2. **Linear Regression**

---

## 📊 Conclusion

Multiple regression models were trained and compared. Random Forest Regression emerged as the best-performing model, achieving the lowest weighted final sMAPE during cross-validation. This indicates strong predictive performance to the data’s characteristics.

Due to the absence of target values in the provided test set, model evaluation was based on cross-validation scores. The final trained model was used to generate predictions for the test set, formatted according to the project requirements and saved for submission.

Key takeaways:

Careful feature engineering and selection are critical for building effective models in industrial process data.
Cross-validation is essential for reliable performance estimation when ground truth is unavailable for the test set.
The Random Forest Regression model is recommended for deployment or further refinement based on its superior performance.


🚀 **Future Work:** Further model optimization, feature engineering, and testing alternative machine learning approaches could help refine predictions even further.

