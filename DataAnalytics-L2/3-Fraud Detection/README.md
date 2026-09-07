# Fraud Detection Using Machine Learning

## 📌 Project Overview

This project focuses on building a machine learning pipeline to detect **fraudulent financial transactions** from a heavily imbalanced dataset.

Fraud detection is a challenging classification problem because fraudulent transactions usually represent only a small percentage of all transactions. Therefore, this project focuses not only on model training but also on handling **class imbalance** and selecting appropriate evaluation metrics.

Two machine learning models are trained and compared:

* Logistic Regression
* Random Forest

**SMOTE (Synthetic Minority Oversampling Technique)** is used to address class imbalance in the training data.

---

## 🎯 Objective

Build a machine learning pipeline capable of identifying fraudulent transactions while addressing the challenges caused by highly imbalanced financial transaction data.

The project aims to:

* Analyze fraud vs. non-fraud transactions
* Understand class imbalance
* Perform exploratory data analysis
* Apply SMOTE for minority-class oversampling
* Train multiple classification models
* Evaluate models using fraud-focused metrics
* Analyze important features
* Discuss scalability for high-volume transactions

---

## 🛠️ Tech Stack

* **Python**
* **Pandas** – Data manipulation and analysis
* **NumPy** – Numerical operations
* **Scikit-learn** – Machine learning
* **Imbalanced-learn** – SMOTE oversampling
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization
* **Jupyter Notebook** – Development environment

### Machine Learning Models

* Logistic Regression
* Random Forest Classifier

---

## 📂 Project Structure

```text
DataAnalytics-L2-FraudDetection/
│
├── Fraud_Detection.ipynb
├── README.md
├── requirements.txt
│
├── dataset/
│   └── fraud_transactions.csv
│
└── screenshots/
    ├── class_distribution.png
    ├── transaction_amount_distribution.png
    ├── time_analysis.png
    ├── confusion_matrix_lr.png
    ├── confusion_matrix_rf.png
    ├── roc_curve.png
    ├── feature_importance.png
    └── model_comparison.png
```

---

# 📊 Dataset

The dataset contains financial transaction records along with a target variable indicating whether a transaction is fraudulent.

The target variable generally contains two classes:

* **0 → Non-Fraudulent**
* **1 → Fraudulent**

The dataset is expected to be highly imbalanced, with fraudulent transactions forming a small percentage of the total transactions.

The exact fraud percentage is calculated during the notebook analysis.

---

# 🔍 Project Workflow

## 1. Load and Inspect Dataset

The dataset is loaded using Pandas.

Initial inspection includes:

* Number of rows and columns
* Column names
* Data types
* Missing values
* Duplicate records
* Descriptive statistics
* Target class distribution

Example:

```python
import pandas as pd

df = pd.read_csv("dataset/fraud_transactions.csv")

print(df.head())
print(df.shape)
print(df.info())
print(df.isnull().sum())
print(df.describe())
```

---

# ⚖️ 2. Class Imbalance Analysis

The distribution of fraudulent and non-fraudulent transactions is analyzed.

```python
df["Class"].value_counts()
```

The percentage of fraudulent transactions is calculated to understand the severity of the imbalance.

```python
fraud_percentage = df["Class"].mean() * 100

print("Fraud percentage:", fraud_percentage)
```

### Why is class imbalance a problem?

In a heavily imbalanced dataset, the model may become biased toward the majority class.

For example, if only a very small percentage of transactions are fraudulent, a model could predict almost every transaction as non-fraudulent and still achieve very high accuracy.

However, such a model would fail at the most important task: **detecting fraud**.

---

# ⚠️ 3. Why Accuracy Can Be Misleading

Accuracy alone is not an appropriate metric for heavily imbalanced fraud detection problems.

Consider a dataset where:

* 99% of transactions are legitimate
* 1% are fraudulent

A model that predicts every transaction as legitimate could achieve approximately 99% accuracy while detecting **zero fraudulent transactions**.

Therefore, this project focuses on:

* Precision
* Recall
* F1-Score
* AUC-ROC

These metrics provide a much better understanding of fraud detection performance.

---

# 📈 4. Exploratory Data Analysis

EDA is performed to understand transaction behavior.

## Transaction Amount Analysis

Transaction amounts are compared between:

* Fraudulent transactions
* Non-fraudulent transactions

Visualization helps identify whether fraudulent transactions show different amount patterns.

---

## Time-of-Day Analysis

Transaction timing is analyzed to identify potential differences between fraudulent and legitimate transactions.

This can help answer questions such as:

* Are fraudulent transactions more common during certain hours?
* Are unusual transaction times associated with fraud?
* Do fraud patterns change throughout the day?

The exact findings depend on the dataset.

---

# 🧹 5. Data Preprocessing

Before model training, the dataset is prepared by:

* Handling missing values
* Checking duplicate records
* Selecting relevant features
* Separating features and target
* Preparing numerical variables for modeling

Data preprocessing decisions are documented in the notebook.

---

# ✂️ 6. Train/Test Split

The dataset is divided into:

* **80% Training Data**
* **20% Testing Data**

Stratification is used to ensure that fraudulent transactions are represented in both sets.

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.20,
    random_state=42,
    stratify=y
)
```

Using stratification is particularly important because the fraud class is rare.

---

# 🔄 7. Handling Class Imbalance Using SMOTE

**SMOTE (Synthetic Minority Oversampling Technique)** is applied to the training data to increase representation of the minority fraud class.

SMOTE generates synthetic examples of minority-class observations rather than simply duplicating existing records.

Example:

```python
from imblearn.over_sampling import SMOTE

smote = SMOTE(random_state=42)

X_train_resampled, y_train_resampled = smote.fit_resample(
    X_train,
    y_train
)
```

### Important

SMOTE is applied **only to the training data**.

The test dataset remains untouched so that model performance can be evaluated on the original class distribution.

---

# 🤖 8. Model 1 — Logistic Regression

Logistic Regression is used as one of the baseline classification models.

It is useful because it is:

* Simple
* Fast
* Interpretable
* Suitable for binary classification

```python
from sklearn.linear_model import LogisticRegression

lr_model = LogisticRegression(
    max_iter=1000,
    random_state=42
)

lr_model.fit(X_train_resampled, y_train_resampled)

lr_pred = lr_model.predict(X_test)
lr_prob = lr_model.predict_proba(X_test)[:, 1]
```

---

# 🌲 9. Model 2 — Random Forest

Random Forest is an ensemble learning algorithm that combines multiple decision trees.

It can capture nonlinear relationships between transaction features and fraud probability.

Advantages include:

* Handles nonlinear relationships
* Robust to complex feature interactions
* Provides feature importance
* Suitable for classification problems

```python
from sklearn.ensemble import RandomForestClassifier

rf_model = RandomForestClassifier(
    n_estimators=100,
    random_state=42,
    n_jobs=-1
)

rf_model.fit(X_train_resampled, y_train_resampled)

rf_pred = rf_model.predict(X_test)
rf_prob = rf_model.predict_proba(X_test)[:, 1]
```

---

# 📏 10. Model Evaluation

The models are evaluated using fraud-focused metrics.

## Precision

Precision measures how many transactions predicted as fraudulent were actually fraudulent.

High precision means fewer legitimate transactions are incorrectly flagged as fraud.

---

## Recall

Recall measures how many actual fraudulent transactions were successfully detected.

High recall means fewer fraudulent transactions are missed.

---

## F1-Score

F1-score provides a balance between precision and recall.

It is especially useful when both false positives and false negatives matter.

---

## AUC-ROC

The ROC curve evaluates the model's ability to distinguish between fraudulent and legitimate transactions across different classification thresholds.

A higher AUC generally indicates better class-separation ability.

---

# 🔲 11. Confusion Matrix

A confusion matrix is generated for each model.

It contains:

* True Positives (TP)
* True Negatives (TN)
* False Positives (FP)
* False Negatives (FN)

For fraud detection, **False Negatives are particularly important** because they represent fraudulent transactions that the system failed to detect.

---

# ⚖️ 12. Precision vs. Recall Trade-Off

There is an important trade-off between Precision and Recall.

### If Recall is prioritized

The model attempts to detect as many fraudulent transactions as possible.

**Advantage:** Fewer fraud cases are missed.

**Disadvantage:** More legitimate transactions may be incorrectly flagged.

### If Precision is prioritized

The model makes fraud alerts more reliable.

**Advantage:** Fewer legitimate transactions are flagged.

**Disadvantage:** Some fraudulent transactions may be missed.

### Which metric matters most?

For many fraud detection applications, **Recall is particularly important** because missing a fraudulent transaction can result in direct financial loss.

However, extremely high recall with very low precision can generate too many false alarms.

Therefore, the appropriate threshold should be selected based on the business cost of:

* Missing fraud
* Investigating legitimate transactions

The **F1-score and Precision-Recall trade-off** should also be considered.

---

# 🌲 13. Feature Importance

Random Forest provides feature importance values that help identify which transaction features contribute most to fraud prediction.

```python
import pandas as pd

feature_importance = pd.Series(
    rf_model.feature_importances_,
    index=X.columns
).sort_values(ascending=False)

print(feature_importance)
```

A bar chart is created to visualize the most important features.

The exact ranking depends on the dataset and trained model.

---

# 📊 14. Model Comparison

The performance of both models is summarized in a comparison table.

| Model               |      Precision |         Recall |       F1-Score |        AUC-ROC |
| ------------------- | -------------: | -------------: | -------------: | -------------: |
| Logistic Regression | Dataset result | Dataset result | Dataset result | Dataset result |
| Random Forest       | Dataset result | Dataset result | Dataset result | Dataset result |

The actual values are generated after executing the notebook.

---

# 🚀 15. Scalability

A real-world fraud detection system may need to process extremely large transaction volumes, potentially reaching **1 million transactions per hour**.

This corresponds to roughly **278 transactions per second** on average.

To handle such workloads, the system could use:

### Efficient Data Processing

Use optimized numerical operations and efficient feature-processing pipelines.

### Batch or Streaming Architecture

Transactions can be processed using streaming technologies or distributed processing systems.

### Parallel Processing

Random Forest supports parallel computation through multiple CPU cores.

### Low-Latency Prediction

A trained model can be deployed as an API or integrated directly into a transaction-processing service.

### Model Monitoring

The production system should continuously monitor:

* Fraud detection rate
* False positives
* False negatives
* Data drift
* Model performance
* Prediction latency

### Periodic Retraining

Fraud patterns change over time, so the model should be retrained periodically using recent transaction data.

---

# 📸 Project Visualizations

The project includes:

1. Fraud vs. non-fraud class distribution
2. Transaction amount distribution
3. Time-of-day analysis
4. Logistic Regression confusion matrix
5. Random Forest confusion matrix
6. ROC curve comparison
7. Random Forest feature importance
8. Model performance comparison

---

# 💡 Key Insights

This project helps identify:

* The percentage of fraudulent transactions
* The severity of class imbalance
* Differences between fraudulent and legitimate transaction amounts
* Time-based fraud patterns
* The impact of SMOTE on minority-class learning
* Performance differences between Logistic Regression and Random Forest
* Important features associated with fraud detection
* The trade-off between fraud detection and false alarms

The final numerical results and insights are based on the dataset used in the notebook.

---

# 🔑 Skills Demonstrated

* Python
* Pandas
* NumPy
* Exploratory Data Analysis
* Data Preprocessing
* Class Imbalance Analysis
* SMOTE
* Stratified Train/Test Split
* Logistic Regression
* Random Forest
* Precision
* Recall
* F1-Score
* AUC-ROC
* Confusion Matrix
* Feature Importance
* Model Comparison
* Machine Learning
* Fraud Detection
* Scalability Analysis

---

# 📋 Requirements

Install the required libraries using:

```bash
pip install -r requirements.txt
```

### requirements.txt

```text
pandas
numpy
scikit-learn
imbalanced-learn
matplotlib
seaborn
jupyter
```

---

# 👨‍💻 Author

**Ratnesh Chauhan**

**OIBSIP – Data Analytics Internship**

---

# 📝 Conclusion

This project demonstrates an end-to-end machine learning pipeline for detecting fraudulent financial transactions in a heavily imbalanced dataset.

The project addresses class imbalance using **SMOTE**, trains **Logistic Regression** and **Random Forest** classifiers, and evaluates them using Precision, Recall, F1-Score, and AUC-ROC rather than relying solely on accuracy.

Feature importance analysis provides additional insight into the factors contributing to fraud predictions. The scalability discussion also considers how such a system could be adapted for high-volume, real-time transaction processing.

The final model should be selected based on the actual evaluation results and the business cost of missed fraud versus false fraud alerts.
