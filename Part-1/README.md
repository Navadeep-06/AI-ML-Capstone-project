# 🏡 Part 1 – Data Acquisition, Cleaning & Exploratory Data Analysis

> **Applied AI & ML Essentials – Capstone Project**  
> **Track:** Data Preparation & Exploratory Data Analysis

---

## 📌 Project Overview

This project focuses on preparing the **Bangalore House Price Dataset** for machine learning by performing comprehensive data cleaning and exploratory data analysis (EDA).

The primary objective is to transform raw housing data into a clean, reliable, and analysis-ready dataset that can be used for predictive modeling in subsequent parts of the capstone project.

---

# 📂 Dataset Information

| Attribute | Details |
|-----------|----------|
| Dataset | Bangalore House Price Dataset |
| Input File | `housing.csv` |
| Output File | `cleaned_data.csv` |
| Target Variable | **price** |

### 📊 Key Features

- Area Type
- Availability
- Location
- Size
- Society
- Total Square Feet
- Number of Bathrooms
- Number of Balconies

---

# ✅ Tasks Performed

## 1️⃣ Data Loading

✔ Loaded the dataset using Pandas.

✔ Displayed

- First 5 rows
- Data types
- Dataset shape

---

## 2️⃣ Missing Value Analysis

Performed a detailed missing value analysis by calculating:

- Missing value count
- Missing value percentage

### ✔ Imputation Strategy

- Numerical columns having less than **20% missing values** were filled using the **Median**.

### 💡 Why Median?

Median is less affected by extreme values and skewed distributions, making it a better choice than the mean for housing price data.

---

## 3️⃣ Duplicate Detection

Performed duplicate analysis using:

```python
df.duplicated().sum()
```

✔ Removed duplicate records.

✔ Verified the updated dataset size.

---

## 4️⃣ Data Type Correction

Performed data type optimization by:

- Converting incorrect numeric columns
- Converting repetitive string columns into **Category** datatype
- Comparing memory usage before and after conversion

---

## 5️⃣ Descriptive Statistics & Skewness

Generated descriptive statistics using:

```python
df.describe()
```

Calculated skewness for all numerical features.

✔ Identified the most skewed feature.

---

## 6️⃣ Outlier Detection (IQR Method)

Applied the **Interquartile Range (IQR)** method on selected numerical columns.

Computed:

- Q1
- Q3
- IQR
- Lower Bound
- Upper Bound
- Number of Outliers

### ✔ Decision

Outliers were **retained** because they may represent valid premium properties and tree-based machine learning models are generally robust to outliers.

---

# 📈 Exploratory Data Analysis

The following visualizations were created:

📉 Line Plot

📊 Bar Chart

📈 Histogram

🔵 Scatter Plot

📦 Box Plot

🔥 Correlation Heatmap

Each visualization contains proper:

- Title
- Axis Labels
- Interpretation

---

# 🔍 Correlation Analysis

Computed the **Pearson Correlation Matrix** and visualized it using a heatmap.

The strongest correlated numerical features were identified and analyzed.

---

# 📊 Additional Statistical Analysis

## 🔹 Mean vs Median Comparison

Compared the **Mean** and **Median** of the two most skewed numerical columns.

This comparison justified selecting the **Median** for missing value imputation.

---

## 🔹 Spearman Rank Correlation

Computed both:

- Pearson Correlation
- Spearman Correlation

Compared both matrices to identify monotonic relationships between numerical features.

---

## 🔹 Grouped Aggregation

Performed grouped aggregation using:

- One categorical feature
- One numerical feature

Calculated:

- Mean
- Standard Deviation
- Count

---

# 📁 Output Files

```
Part-1/
│
├── data_prep_eda.ipynb
├── cleaned_data.csv
├── README.md
│
└── Plots/
    ├── line_plot.png
    ├── bar_chart.png
    ├── histogram.png
    ├── scatter_plot.png
    ├── box_plot.png
    └── correlation_heatmap.png
```

---

# 🛠 Technologies Used

- 🐍 Python
- 🐼 Pandas
- 🔢 NumPy
- 📊 Matplotlib
- 🎨 Seaborn

---

# ▶️ How to Run

### Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn
```

### Run Notebook

```bash
jupyter notebook data_prep_eda.ipynb
```

The cleaned dataset will automatically be saved as:

```
cleaned_data.csv
```

---

# 📌 Key Findings

✔ Missing values were successfully handled.

✔ Duplicate records were removed.

✔ Data types were optimized.

✔ Skewed features were identified.

✔ Outliers were documented using the IQR method.

✔ Correlation analysis revealed important relationships among numerical features.

✔ The cleaned dataset is ready for machine learning.

---

# 🎯 Conclusion

The raw housing dataset was successfully cleaned, validated, and explored through comprehensive exploratory data analysis.

Data quality issues such as missing values, duplicate records, incorrect data types, and outliers were addressed using appropriate preprocessing techniques. Statistical analysis and visualizations provided valuable insights into feature distributions and relationships.

The resulting **`cleaned_data.csv`** is fully prepared for feature engineering and machine learning tasks in **Part 2** of the Applied AI & ML Essentials Capstone Project.

---

## 👨‍💻 Author

**Navadeep P R**

Applied AI & ML Essentials Capstone Project