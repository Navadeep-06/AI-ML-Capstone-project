# 🤖 Part 2 – Supervised Machine Learning Model

---

## 📌 Project Overview

This project focuses on building, training, and evaluating supervised machine learning models using the cleaned dataset generated in **Part 1**. Both regression and classification models were developed following proper preprocessing techniques to avoid data leakage and improve model performance.

---

## 🎯 Objectives

- Load the cleaned dataset from Part 1
- Perform feature preprocessing
- Build Regression and Classification models
- Compare multiple machine learning algorithms
- Perform Cross Validation
- Tune hyperparameters using GridSearchCV
- Analyze feature importance
- Save the best-performing model for deployment

---

## 📂 Dataset

**Input File**

`cleaned_data.csv`

### Target Variables

- **Regression Target (y_reg):** `price`
- **Classification Target (y_clf):**
  - 1 → Price ≥ Median Price
  - 0 → Price < Median Price

---

## ⚙️ Data Preprocessing

### ✅ Missing Value Handling

Missing numerical values were filled using the **Median** because it is less affected by outliers than the mean.

### ✅ Categorical Encoding

Categorical variables were converted into numerical format using **One-Hot Encoding (`pd.get_dummies`)** with `drop_first=True`.

This prevents introducing false ordinal relationships while avoiding multicollinearity.

### ✅ Train-Test Split

The dataset was divided into:

- 📚 Training Data → 80%
- 🧪 Testing Data → 20%

using:

```python
train_test_split(test_size=0.2, random_state=42)
```

### ✅ Feature Scaling

Standardization was performed using **StandardScaler**.

The scaler was fitted **only on the training data** and then applied to the testing data to prevent **data leakage**.

---

# 📈 Regression Models

## 🔹 Linear Regression

The Linear Regression model was trained to predict house prices.

Evaluation Metrics:

- Mean Squared Error (MSE)
- R² Score

---

## 🔹 Ridge Regression

A Ridge Regression model was trained using L2 Regularization (`alpha=1.0`).

### Why Ridge Regression?

Ridge Regression reduces overfitting by shrinking coefficient values while maintaining all features in the model.

The performance of Ridge Regression was compared with Linear Regression using:

- MSE
- R² Score

---

# 🏷️ Classification Models

Several classification models were implemented and compared.

### 🌳 Decision Tree

Different Decision Tree models were trained using:

- Default Tree
- Tuned Tree
- Gini Criterion
- Entropy Criterion

Hyperparameters like **max_depth** and **min_samples_split** were adjusted to reduce overfitting.

---

### 🌲 Random Forest

Random Forest was trained using:

- 100 Trees
- Maximum Depth = 10

Evaluation Metrics:

- Accuracy
- ROC-AUC Score

Feature importance was also extracted to identify the most influential variables.

---

### 🚀 Gradient Boosting

Gradient Boosting Classifier was implemented and evaluated using:

- Accuracy
- ROC-AUC Score

---

### 📊 Logistic Regression

Logistic Regression served as the baseline classification model.

Evaluation Metrics:

- Accuracy
- Precision
- Recall
- F1 Score
- ROC-AUC

---

# 🌟 Feature Importance

Random Forest Feature Importance was computed.

The **Top Important Features** and **Least Important Features** were identified.

The five least important features were removed, and a reduced Random Forest model was trained to compare performance with the original model.

---

# 🔄 Cross Validation

To evaluate model robustness, **Stratified K-Fold Cross Validation (5 folds)** was performed.

Models Evaluated:

- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting

Evaluation Metric:

- ROC-AUC

Both Mean AUC and Standard Deviation were reported.

---

# 🎯 Hyperparameter Tuning

GridSearchCV was used to optimize the Random Forest Pipeline.

Parameters Tuned:

- Number of Trees
- Maximum Depth
- Minimum Samples per Leaf

Scoring Metric:

- ROC-AUC

The best parameter combination was automatically selected.

---

# 📈 Learning Curve Analysis

The best model was trained using different fractions of the training dataset:

- 20%
- 40%
- 60%
- 80%
- 100%

Training AUC and Test AUC were compared to analyze learning behaviour and detect possible overfitting.

---

# 💾 Model Saving

The best model obtained from GridSearchCV was saved using **Joblib**.

```python
joblib.dump(best_pipeline, "best_model.pkl")
```

The saved model was reloaded successfully using:

```python
joblib.load("best_model.pkl")
```

Predictions after loading confirmed that the model serialization process was successful.

---

# 📊 Performance Metrics Used

### Regression

- Mean Squared Error (MSE)
- R² Score

### Classification

- Accuracy
- Precision
- Recall
- F1 Score
- ROC-AUC

Cross Validation was additionally used to measure model stability.

---

# 📁 Project Structure

```
Part-2/
│── supervised_model.ipynb
│── cleaned_data.csv
│── best_model.pkl
│── README.md
```

---

# ✅ Conclusion

This project successfully demonstrates a complete supervised machine learning workflow from preprocessing to model deployment.

✔ Data preprocessing without leakage

✔ Feature encoding and scaling

✔ Regression and classification model development

✔ Feature importance analysis

✔ Cross Validation

✔ Hyperparameter tuning using GridSearchCV

✔ Learning curve evaluation

✔ Model serialization using Joblib

The **Random Forest Pipeline** achieved the best overall performance and was saved as **best_model.pkl**, which is later used in **Part 4** for LLM-powered model explanation.