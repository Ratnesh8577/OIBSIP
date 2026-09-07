# Data Cleaning and Preprocessing

## 📌 Project Overview

This project demonstrates professional-level data cleaning and preprocessing using Python. A deliberately messy dataset is systematically transformed into a clean, consistent, and analysis-ready dataset.

The project focuses on identifying data-quality issues, handling missing values, removing duplicates, standardizing inconsistent data, detecting outliers, correcting data types, and documenting every cleaning decision.

---

## 🎯 Objective

Demonstrate professional-level data cleaning skills by taking a deliberately messy dataset and systematically transforming it into a clean, reliable, and analysis-ready dataset.

---

## 🛠️ Tech Stack

* **Python**
* **Pandas** – Data manipulation and cleaning
* **NumPy** – Numerical operations
* **Jupyter Notebook** – Data analysis and documentation

---

## 📂 Project Structure

```text
DataAnalytics-L1-DataCleaning/
│
├── Data_Cleaning.ipynb
├── README.md
├── requirements.txt
│
├── dataset/
│   ├── messy_dataset.csv
│   └── cleaned_dataset.csv
│
└── screenshots/
    ├── data_quality_report.png
    ├── outlier_analysis.png
    └── before_after_summary.png
```

---

## 🔍 Data Cleaning Workflow

### 1. Dataset Loading

The original messy dataset is loaded using Pandas and inspected to understand its structure and quality.

### 2. Data Quality Report

A comprehensive data-quality report is created containing:

* Number of rows and columns
* Null values per column
* Duplicate rows
* Data types
* Potential data type issues
* Minimum and maximum values
* Value-range anomalies

---

## 🧹 Missing Data Handling

Missing values are analyzed on a column-by-column basis.

Different strategies are considered depending on the characteristics of each column:

* Mean imputation
* Median imputation
* Mode imputation
* Forward fill
* Row deletion

Each decision is documented in the notebook with a justification.

For example, median imputation may be preferred for numerical columns containing outliers because the median is less sensitive to extreme values.

---

## ♻️ Duplicate Removal

Duplicate records are identified and removed from the dataset.

The notebook documents:

* Number of duplicate rows before cleaning
* Number of duplicates removed
* Number of rows remaining after cleaning

---

## 🔄 Data Standardisation

Inconsistent values and formatting are standardized to ensure consistency across the dataset.

Examples include:

* `"Male"`, `"male"`, `"M"` → `"Male"`
* `"Female"`, `"female"`, `"F"` → `"Female"`
* Standardizing text capitalization
* Removing unnecessary whitespace
* Converting inconsistent date formats into `datetime`

---

## 📊 Outlier Detection

Outliers in numerical columns are identified using the **Interquartile Range (IQR)** method.

The general process includes:

1. Calculate Q1
2. Calculate Q3
3. Calculate IQR
4. Determine lower and upper bounds
5. Identify observations outside the bounds

Outliers are then evaluated individually to determine whether they should be:

* Retained
* Capped
* Removed

The reasoning for each decision is documented in the notebook.

---

## 🔢 Data Type Correction

All columns are converted to appropriate data types.

Examples:

| Data                | Expected Type     |
| ------------------- | ----------------- |
| Customer/Record IDs | `string`          |
| Dates               | `datetime`        |
| Monetary values     | `float`           |
| Quantities          | `integer`         |
| Categorical values  | `string/category` |

Correct data types improve consistency and make the cleaned dataset suitable for further analysis.

---

## 📋 Before vs After Data Quality Summary

A comparison is created to demonstrate the improvement in data quality.

| Metric           |   Before Cleaning |    After Cleaning |
| ---------------- | ----------------: | ----------------: |
| Row Count        | Dataset-dependent | Dataset-dependent |
| Null Count       | Dataset-dependent | Dataset-dependent |
| Duplicate Count  | Dataset-dependent | Dataset-dependent |
| Data Type Issues | Dataset-dependent | Dataset-dependent |
| Outliers         | Dataset-dependent | Dataset-dependent |

The actual values are calculated directly from the dataset in the notebook.

---

## 💾 Output

After completing the cleaning process, the final analysis-ready dataset is saved as:

```text
dataset/cleaned_dataset.csv
```

Example:

```python
df.to_csv("dataset/cleaned_dataset.csv", index=False)
```

---

## 📈 Key Skills Demonstrated

* Data Quality Assessment
* Missing Value Handling
* Duplicate Detection
* Data Standardisation
* Outlier Detection
* IQR Method
* Data Type Conversion
* Data Validation
* Data Preprocessing
* Documentation of Data Cleaning Decisions
* Pandas and NumPy

---

## 🚀 Expected Outcome

The final output is a clean, consistent, and analysis-ready dataset with:

* Reduced missing data
* No unintended duplicate records
* Consistent formatting
* Correct data types
* Properly evaluated outliers
* Documented cleaning decisions

---

## 👨‍💻 Author

**Ratnesh Chauhan**

**OIBSIP – Data Analytics Internship**

---

## 📝 Conclusion

Data cleaning is an essential step in any data analysis or machine learning workflow. This project demonstrates a systematic approach to identifying and resolving common data-quality problems while documenting the reasoning behind each decision.

The resulting cleaned dataset can be confidently used for further exploratory analysis, visualization, reporting, or machine learning tasks.
