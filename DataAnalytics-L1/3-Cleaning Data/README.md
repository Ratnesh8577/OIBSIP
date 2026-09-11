# 🧹 Data Cleaning and Preprocessing

## 📌 Project Overview

This project focuses on **Data Cleaning and Preprocessing** using **Python, Pandas, NumPy, and Jupyter Notebook**.

The objective is to transform a raw dataset into a **clean, consistent, validated, and analysis-ready dataset** by identifying and handling missing values, duplicate records, inconsistent formatting, incorrect data types, and potential numerical outliers.

The complete workflow follows a systematic data-quality process from **raw data inspection to final cleaned dataset export**.

---

## 🎯 Objectives

* Load and inspect the raw dataset.
* Create a comprehensive **Data Quality Report**.
* Identify and handle missing values.
* Detect and remove duplicate rows.
* Standardise inconsistent categorical and text values.
* Correct inappropriate data types.
* Detect numerical outliers using the **IQR method**.
* Decide whether outliers should be retained, capped, or removed.
* Compare the dataset before and after cleaning.
* Validate the final cleaned dataset.
* Export the cleaned dataset as a new CSV file.

---

## 🛠️ Tech Stack

* 🐍 **Python**
* 🐼 **Pandas**
* 🔢 **NumPy**
* 📓 **Jupyter Notebook**

---

## 📂 Project Structure

```text
Data-Cleaning-and-Preprocessing/
│
├── 📓 Data_Cleaning_Preprocessing.ipynb
├── 📄 tested(1).csv
├── 📄 tested_cleaned.csv
└── 📄 README.md
```

---

## 🔄 Data Cleaning Workflow

```text
Raw Dataset
     ↓
Load Dataset
     ↓
Inspect Structure
     ↓
Data Quality Report
     ↓
Missing Value Analysis
     ↓
Duplicate Detection
     ↓
Standardisation
     ↓
Data Type Correction
     ↓
Outlier Detection
     ↓
Outlier Treatment Decision
     ↓
Before vs After Comparison
     ↓
Final Validation
     ↓
Export Cleaned Dataset
```

---

# 🔍 1. Data Quality Assessment

The initial dataset was inspected using Pandas to understand its structure and identify potential data-quality issues.

The following checks were performed:

* Dataset shape
* Column names
* Data types
* Missing values
* Duplicate rows
* Unique values
* Numerical ranges
* Potential invalid values

### Key checks

```python
df.info()
df.describe()
df.isnull().sum()
df.duplicated().sum()
```

---

# 🕳️ 2. Missing Data Handling

Missing values were analyzed column by column and an appropriate strategy was selected based on the type and characteristics of each variable.

### Strategy

| Column        | Issue               | Treatment         | Reason                            |
| ------------- | ------------------- | ----------------- | --------------------------------- |
| `Age`         | Missing values      | Median imputation | Reduces influence of extreme ages |
| `Fare`        | Missing value       | Median imputation | Only one missing value            |
| `Cabin`       | Many missing values | `"Unknown"`       | Avoids unnecessary row deletion   |
| Other columns | No missing values   | No action         | Already complete                  |

### Example

```python
df["Age"] = df["Age"].fillna(df["Age"].median())
df["Fare"] = df["Fare"].fillna(df["Fare"].median())
df["Cabin"] = df["Cabin"].fillna("Unknown")
```

After treatment, the dataset was checked again to ensure that no unintended missing values remained.

---

# 🔁 3. Duplicate Removal

Duplicate rows were identified using:

```python
df.duplicated().sum()
```

No duplicate rows were found in the dataset.

The duplicate-removal step was still included in the workflow:

```python
df = df.drop_duplicates()
df = df.reset_index(drop=True)
```

### Result

* Duplicate rows before cleaning: **0**
* Duplicate rows removed: **0**
* Duplicate rows after cleaning: **0**

---

# 🧹 4. Standardisation

Text values were standardised to ensure consistent formatting.

### Operations performed

* Removed leading and trailing spaces.
* Standardised gender values.
* Standardised `Embarked` codes.
* Cleaned text fields.
* Converted identifier columns to string.

### Example

```python
df["Sex"] = (
    df["Sex"]
    .astype("string")
    .str.strip()
    .str.lower()
    .replace({
        "m": "Male",
        "male": "Male",
        "f": "Female",
        "female": "Female"
    })
)
```

For `Embarked`:

```python
df["Embarked"] = (
    df["Embarked"]
    .astype("string")
    .str.strip()
    .str.upper()
)
```

The dataset does not contain a date column, so datetime conversion was not required.

---

# 🔢 5. Data Type Correction

Data types were reviewed and corrected according to the meaning of each column.

### Examples

| Column        | Correct Type |
| ------------- | ------------ |
| `PassengerId` | String       |
| `Survived`    | Integer      |
| `Pclass`      | Integer      |
| `Name`        | String       |
| `Sex`         | String       |
| `Age`         | Float        |
| `SibSp`       | Integer      |
| `Parch`       | Integer      |
| `Ticket`      | String       |
| `Fare`        | Float        |
| `Cabin`       | String       |
| `Embarked`    | String       |

Identifiers such as `PassengerId` and `Ticket` were treated as **strings rather than numerical measurements**.

---

# 📊 6. Outlier Detection

Potential outliers were identified using the **Interquartile Range (IQR)** method.

The IQR method was applied to numerical columns.

```python
Q1 = df[column].quantile(0.25)
Q3 = df[column].quantile(0.75)

IQR = Q3 - Q1

lower_limit = Q1 - 1.5 * IQR
upper_limit = Q3 + 1.5 * IQR
```

Values below the lower limit or above the upper limit were identified as potential outliers.

### Potential outliers were identified in:

* `Age`
* `SibSp`
* `Parch`
* `Fare`

---

# ⚖️ 7. Outlier Treatment Decision

The identified outliers were **retained** rather than automatically removed.

This decision was made because extreme values can represent legitimate passenger characteristics.

For example:

* A passenger may legitimately have a high fare.
* A passenger may legitimately be older.
* Some passengers may have several siblings or spouses.
* Some passengers may have multiple parents or children.

Therefore, removing these observations could result in unnecessary information loss.

---

# 📋 8. Before vs After Cleaning

A comparison table was created to measure the impact of the cleaning process.

| Metric         |     Before Cleaning | After Cleaning |
| -------------- | ------------------: | -------------: |
| Rows           |                 418 |            418 |
| Columns        |                  12 |             12 |
| Missing Values |                 414 |              0 |
| Duplicate Rows |                   0 |              0 |
| Data Types     | Required correction |      Corrected |

The cleaning process removed missing-value issues while preserving valid observations.

---

# ✅ 9. Final Validation

The final dataset was validated using:

```python
print("Rows:", df.shape[0])
print("Columns:", df.shape[1])
print("Missing values:", df.isnull().sum().sum())
print("Duplicate rows:", df.duplicated().sum())
print(df.dtypes)
```

### Final quality checks

* ✅ No missing values
* ✅ No duplicate rows
* ✅ Consistent categorical formatting
* ✅ Correct numerical data types
* ✅ Identifier fields stored appropriately
* ✅ Potential outliers reviewed
* ✅ Dataset structure preserved

---

# 💾 10. Export Cleaned Dataset

The cleaned dataset was exported to a new CSV file so that the original raw dataset remained unchanged.

```python
df.to_csv(
    "tested_cleaned.csv",
    index=False
)
```

Output:

```text
tested_cleaned.csv
```

---

# 📈 Results

The data-cleaning process successfully converted the raw dataset into a cleaner and more analysis-ready dataset.

### Summary

* **418** original records
* **12** columns
* **414** missing cells handled
* **0** duplicate rows
* Inconsistent text formatting standardised
* Data types corrected
* Potential numerical outliers identified using IQR
* Legitimate extreme values retained
* Cleaned dataset exported successfully

---

# 🎓 Key Learning Outcomes

Through this project, I practiced:

* Data quality assessment
* Missing-value analysis
* Median imputation
* Missing categorical value handling
* Duplicate detection
* Text standardisation
* Data type conversion
* IQR-based outlier detection
* Data validation
* Before-and-after data comparison
* CSV data export
* Pandas and NumPy data manipulation

---

# 🚀 Future Improvements

The project can be extended with:

* Exploratory Data Analysis (EDA)
* Data visualisation using Matplotlib and Seaborn
* Correlation analysis
* Feature engineering
* Automated data-quality checks
* Statistical analysis
* Machine-learning preprocessing

---

## 👨‍💻 Author

**Ratnesh Chauhan**

### 🔗 Connect With Me

* **GitHub:** Ratnesh8577
* **LinkedIn:** Ratnesh Chauhan
* **LeetCode:** RatneshChauhan279

---

## ⭐ Project Summary

> **Clean data is the foundation of reliable analysis.**

This project demonstrates a complete and practical **data cleaning and preprocessing workflow using Python, Pandas, NumPy, and Jupyter Notebook**, preparing raw data for reliable downstream analysis and machine-learning applications.
