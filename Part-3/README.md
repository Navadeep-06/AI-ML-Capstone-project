# 🌳 Part 3 – Advanced Modeling, Ensembles, Hyperparameter Tuning & ML Pipeline 🚀

## 📌 Project Overview
In this part, multiple machine learning classification models were trained and evaluated to identify the best-performing model for predicting housing price categories. Ensemble methods, feature importance analysis, cross-validation, hyperparameter tuning, and model serialization were performed to build a reliable production-ready ML pipeline.

---

# ✅ Tasks Completed

## 🌳 1. Decision Tree Baseline
- Trained an unrestricted Decision Tree Classifier.
- Evaluated Training Accuracy and Testing Accuracy.
- Observed signs of overfitting due to high training accuracy.

---

## 🌲 2. Controlled Decision Tree
- Applied:
  - `max_depth = 5`
  - `min_samples_split = 20`
- Compared performance with the unrestricted tree.
- Reduced overfitting while maintaining good accuracy.

---

## ⚖️ 3. Gini vs Entropy Comparison
Two Decision Tree models were trained using:

- Gini Impurity
- Entropy

### Gini Formula

\[
Gini = 1-\sum p_i^2
\]

### Entropy Formula

\[
Entropy = -\sum p_i \log_2(p_i)
\]

Both models were compared using Test Accuracy.

---

## 🌳 4. Random Forest
Random Forest Classifier was trained with:

- 100 Trees
- Maximum Depth = 10

Evaluation Metrics:
- ✅ Training Accuracy
- ✅ Testing Accuracy
- ✅ ROC-AUC Score

Top important features were extracted using:

```python
feature_importances_
```

---

## 🚀 4a. Gradient Boosting
Gradient Boosting Classifier was trained using:

- n_estimators = 100
- learning_rate = 0.1
- max_depth = 3

Performance was evaluated using:

- Training Accuracy
- Testing Accuracy
- ROC-AUC

---

## ✂️ 4b. Feature Ablation Study
- Identified the 5 least important features.
- Removed them from the dataset.
- Retrained Random Forest.
- Compared ROC-AUC before and after feature removal.

This helps determine whether low-importance features contribute meaningful information.

---

## 📊 5. Cross Validation
Performed 5-Fold Stratified Cross Validation on:

- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting

Evaluation Metric:

- ROC-AUC

Reported:

- Mean AUC
- Standard Deviation

---

## ⚙️ 6. Hyperparameter Tuning
Built an ML Pipeline consisting of:

- SimpleImputer
- StandardScaler
- RandomForestClassifier

Performed GridSearchCV to find the best hyperparameters.

Outputs:
- ✅ Best Parameters
- ✅ Best ROC-AUC Score

---

## 📈 7. Manual Learning Curve
The best pipeline was trained using:

- 20%
- 40%
- 60%
- 80%
- 100%

of the training data.

Training AUC and Test AUC were compared to study model learning behaviour.

---

## 💾 8. Model Serialization
The best trained model was saved using Joblib.

```python
joblib.dump(best_pipeline,"best_model.pkl")
```

The saved model was reloaded successfully and used for prediction.

---

## 🏆 9. Summary Comparison

Among all the models tested, the **Random Forest Pipeline with GridSearchCV** delivered the best overall performance by achieving the highest ROC-AUC score while maintaining good generalization on unseen data. Cross-validation results also showed that the model was stable and consistent across different data splits. Therefore, this tuned Random Forest pipeline is recommended for deployment because it provides a strong balance between accuracy, robustness, and reliability for house price classification.
---

# 🛠️ Libraries Used

- Pandas
- NumPy
- Matplotlib
- Scikit-Learn
- Joblib

---

# 🎯 Outcome

✔ Decision Tree Analysis

✔ Gini vs Entropy Comparison

✔ Random Forest

✔ Gradient Boosting

✔ Feature Importance

✔ Feature Ablation

✔ Cross Validation

✔ Hyperparameter Tuning

✔ Learning Curve Analysis

✔ Model Serialization

✔ Production Ready ML Pipeline

---

# 🏆 Final Conclusion

Random Forest with GridSearchCV provided the best balance between accuracy, ROC-AUC, and generalization performance. The optimized pipeline was serialized using Joblib, making it suitable for future deployment and inference.