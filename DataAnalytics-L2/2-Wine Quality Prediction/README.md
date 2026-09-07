# Wine Quality Prediction Using Machine Learning

## 📌 Project Overview

This project focuses on predicting the quality of wine based on its physicochemical properties using machine learning classification algorithms.

The original wine quality score is typically represented on a scale from **3 to 8**. For classification, the quality scores are grouped into meaningful categories such as **Low, Medium, and High**.

Three machine learning classifiers are trained and compared:

* Random Forest
* Stochastic Gradient Descent (SGD)
* Support Vector Classifier (SVC)

The project demonstrates an end-to-end machine learning workflow, including data exploration, feature engineering, class imbalance analysis, model training, evaluation, and interpretation.

---

## 🎯 Objective

Train and compare multiple classification models to predict wine quality based on physicochemical properties such as:

* Acidity
* Density
* Alcohol
* Sulphates
* pH
* Chlorides
* Residual sugar

The objective is to determine which classification model is most suitable for predicting wine quality.

---

## 🛠️ Tech Stack

* **Python**
* **Pandas** – Data manipulation and analysis
* **NumPy** – Numerical operations
* **Scikit-learn** – Machine learning
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization
* **Jupyter Notebook** – Development environment

### Machine Learning Algorithms

* Random Forest Classifier
* SGD Classifier
* Support Vector Classifier (SVC)

---

## 📂 Project Structure

```text
DataAnalytics-L2-WineQualityPrediction/
│
├── Wine_Quality_Prediction.ipynb
├── README.md
├── requirements.txt
│
├── dataset/
│   └── winequality.csv
│
└── screenshots/
    ├── quality_distribution.png
    ├── feature_distributions.png
    ├── correlation_heatmap.png
    ├── rf_confusion_matrix.png
    ├── sgd_confusion_matrix.png
    ├── svc_confusion_matrix.png
    ├── feature_importance.png
    └── model_comparison.png
```

---

# 📊 Dataset

The Wine Quality dataset contains physicochemical measurements of wine samples along with their quality scores.

Important features include:

* Fixed acidity
* Volatile acidity
* Citric acid
* Residual sugar
* Chlorides
* Free sulfur dioxide
* Total sulfur dioxide
* Density
* pH
* Sulphates
* Alcohol

The **quality** column is used as the target variable.

---

# 🔍 Project Workflow

## 1. Load and Inspect Dataset

The dataset is loaded using Pandas.

Initial inspection includes:

* Dataset shape
* Column names
* Data types
* Missing values
* Duplicate records
* Descriptive statistics
* Quality score distribution

Example:

```python
import pandas as pd

df = pd.read_csv("dataset/winequality.csv")

print(df.head())
print(df.shape)
print(df.info())
print(df.isnull().sum())
print(df.describe())
```

---

## 2. Class Distribution

The distribution of wine quality scores is analyzed to determine whether the classes are balanced.

```python
df["quality"].value_counts().sort_index()
```

A bar chart is created to visualize the number of wines belonging to each quality score.

### Class Imbalance

Wine quality datasets commonly contain more samples in the middle quality ranges than at the extreme ends.

Underrepresented classes can affect machine learning because a model may become biased toward the majority classes and perform poorly on minority classes.

Therefore, class distribution is considered when splitting the dataset and evaluating the models.

---

# 📈 3. Exploratory Data Analysis

EDA is performed to understand the distributions and relationships between physicochemical properties and wine quality.

### Feature Distribution

Distribution plots are created for the chemical features to identify:

* Typical value ranges
* Skewed distributions
* Outliers
* Unusual observations

---

## 4. Correlation Heatmap

A correlation heatmap is created using Seaborn to examine relationships between the physicochemical features and wine quality.

```python
import seaborn as sns
import matplotlib.pyplot as plt

plt.figure(figsize=(12, 8))
sns.heatmap(df.corr(numeric_only=True), annot=True, cmap="coolwarm")
plt.title("Correlation Heatmap")
plt.show()
```

The heatmap helps identify features that have stronger positive or negative relationships with the target variable.

---

# ⚙️ 5. Feature Engineering

The original wine quality score is converted into three classification categories.

### Quality Categories

| Quality Score | Category |
| ------------- | -------- |
| 3–4           | Low      |
| 5–6           | Medium   |
| 7–8           | High     |

This transformation simplifies the prediction problem and creates categories that can be interpreted more easily.

The three-class approach also provides a practical way to distinguish between low-quality, average-quality, and high-quality wines.

---

# ✂️ 6. Train/Test Split

The dataset is divided into:

* **80% Training Data**
* **20% Testing Data**

Stratification is used to preserve the class proportions in both datasets.

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

Using `stratify=y` helps ensure that each class is represented proportionally in the training and testing datasets.

---

# 🤖 7. Machine Learning Models

Three classification algorithms are trained and evaluated.

## Model 1: Random Forest

Random Forest is an ensemble learning algorithm that combines multiple decision trees to make predictions.

It can capture nonlinear relationships and provides feature importance values, making it useful for interpreting which chemical properties contribute most to predictions.

---

## Model 2: SGD Classifier

Stochastic Gradient Descent (SGD) is an efficient optimization-based classifier.

It is useful for large datasets and can provide a relatively fast classification model.

---

## Model 3: Support Vector Classifier

Support Vector Classifier (SVC) attempts to find decision boundaries that effectively separate different classes.

It can be useful when the classes are not easily separated using simple linear relationships.

---

# 📏 8. Model Evaluation

Each model is evaluated using:

* Accuracy
* Precision
* Recall
* F1-score
* Classification Report
* Confusion Matrix

Example:

```python
from sklearn.metrics import accuracy_score, classification_report

accuracy = accuracy_score(y_test, y_pred)

print("Accuracy:", accuracy)
print(classification_report(y_test, y_pred))
```

---

# 🔲 9. Confusion Matrix

A separate confusion matrix is generated for each classifier.

The confusion matrices help identify:

* Correctly predicted Low-quality wines
* Correctly predicted Medium-quality wines
* Correctly predicted High-quality wines
* Misclassified samples

The three confusion matrices allow direct comparison of classification errors between the models.

---

# 🌲 10. Random Forest Feature Importance

Random Forest provides feature importance scores that help identify which physicochemical properties contribute most to the model's predictions.

A feature importance chart is created to rank the chemical properties.

For example, important features may include:

* Alcohol
* Volatile acidity
* Sulphates
* Density
* Citric acid

The exact ranking depends on the dataset and trained model.

---

# 📊 11. Model Comparison

The performance of all three classifiers is summarized in a comparison table.

| Model          |       Accuracy |      Precision |         Recall |       F1-Score |
| -------------- | -------------: | -------------: | -------------: | -------------: |
| Random Forest  | Dataset result | Dataset result | Dataset result | Dataset result |
| SGD Classifier | Dataset result | Dataset result | Dataset result | Dataset result |
| SVC            | Dataset result | Dataset result | Dataset result | Dataset result |

The actual values are obtained after executing the notebook.

---

# 💡 Key Insights

The project helps identify:

* Distribution of different wine quality scores
* Presence of class imbalance
* Relationships between chemical properties
* Important predictors of wine quality
* Differences in classification performance
* Common classification errors
* Most suitable model for deployment

The final numerical insights are based on the actual dataset and model results.

---

# 🚀 Real-World Applications

Wine quality classification can be applied to:

* Automated quality control
* Wine production monitoring
* Quality assurance systems
* Product grading
* Winery decision-making
* Food and beverage analytics
* Predictive quality assessment

---

# 🔑 Skills Demonstrated

* Python
* Pandas
* NumPy
* Exploratory Data Analysis
* Data Visualization
* Feature Engineering
* Class Imbalance Analysis
* Stratified Train/Test Split
* Random Forest
* SGD Classifier
* Support Vector Classifier
* Classification Metrics
* Confusion Matrix
* Feature Importance
* Machine Learning Model Comparison

---

# 📋 Requirements

Install the required Python libraries using:

```bash
pip install -r requirements.txt
```

### requirements.txt

```text
pandas
numpy
scikit-learn
matplotlib
seaborn
jupyter
```

---

# 📸 Project Visualizations

The project includes:

1. Wine quality distribution
2. Chemical feature distributions
3. Correlation heatmap
4. Random Forest confusion matrix
5. SGD confusion matrix
6. SVC confusion matrix
7. Random Forest feature importance
8. Model performance comparison

---

# 👨‍💻 Author

**Ratnesh Chauhan**

**OIBSIP – Data Analytics Internship**

---

# 📝 Conclusion

This project demonstrates how machine learning classification algorithms can be used to predict wine quality based on physicochemical properties.

Random Forest, SGD, and SVC are trained using a stratified train/test split and evaluated using accuracy, precision, recall, F1-score, classification reports, and confusion matrices.

The Random Forest feature importance analysis also provides insight into which chemical properties have the greatest influence on the model's predictions.

Based on the final evaluation results, the model with the strongest overall performance and appropriate computational characteristics can be selected as the most suitable candidate for deployment.
