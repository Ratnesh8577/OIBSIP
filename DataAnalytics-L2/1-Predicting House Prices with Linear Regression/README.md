# House Price Prediction Using Linear Regression

## 📌 Project Overview

This project focuses on building and evaluating a **Linear Regression machine learning model** to predict house prices based on different property-related features such as area, location, number of rooms, and age.

The project demonstrates an end-to-end machine learning workflow, starting from data cleaning and exploratory data analysis (EDA) to feature engineering, model training, evaluation, visualization, and model interpretation.

---

## 🎯 Objective

Build and evaluate a Linear Regression model that predicts house prices based on relevant property features.

The project aims to develop practical skills in:

* Data cleaning
* Exploratory Data Analysis
* Feature selection
* Categorical data encoding
* Machine learning
* Model evaluation
* Data visualization
* Model interpretation

---

## 🛠️ Tech Stack

* **Python**
* **Pandas** – Data manipulation and analysis
* **NumPy** – Numerical operations
* **Scikit-learn** – Machine learning
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization
* **Jupyter Notebook** – Development environment

---

## 📂 Project Structure

```text
DataAnalytics-L2-HousePricePrediction/
│
├── House_Price_Prediction.ipynb
├── README.md
├── requirements.txt
│
├── dataset/
│   └── house_prices.csv
│
└── screenshots/
    ├── price_distribution.png
    ├── correlation_heatmap.png
    ├── actual_vs_predicted.png
    ├── residual_plot.png
    └── coefficient_analysis.png
```

---

## 📊 Dataset

The dataset contains information about residential properties and their prices.

Potential predictive features include:

* **Area** – Size of the property
* **Location** – Geographical location
* **Number of Rooms** – Number of bedrooms/rooms
* **Age** – Age of the property
* **Price** – Target variable

The exact columns depend on the dataset used for the project.

---

# 🔍 Project Workflow

## 1. Load and Inspect the Dataset

The dataset is loaded using Pandas and inspected to understand its structure.

The following checks are performed:

* Number of rows and columns
* Column names
* Data types
* Missing values
* Duplicate records
* Descriptive statistics

Example:

```python
import pandas as pd

df = pd.read_csv("dataset/house_prices.csv")

print(df.head())
print(df.shape)
print(df.info())
print(df.isnull().sum())
print(df.describe())
```

---

## 2. Exploratory Data Analysis

EDA is performed to understand the dataset and identify patterns in house prices.

### Target Variable Distribution

The distribution of the **Price** variable is visualized to understand:

* Price range
* Central tendency
* Spread
* Possible skewness
* Potential outliers

A histogram or distribution plot is used for visualization.

---

## 3. Feature Selection

The features that are likely to influence house prices are identified and discussed.

For example:

| Feature         | Reason                                            |
| --------------- | ------------------------------------------------- |
| Area            | Larger properties generally have higher prices    |
| Location        | Property value can vary significantly by location |
| Number of Rooms | More rooms can increase property value            |
| Age             | Older properties may have different market values |

Feature selection is discussed in a Markdown cell before model training.

---

## 4. Handling Missing Values

Missing values are identified using:

```python
df.isnull().sum()
```

Appropriate strategies are applied depending on the feature, such as:

* Mean/median imputation for numerical features
* Mode imputation for categorical features
* Removing rows where appropriate

The reasoning behind the selected strategy is documented in the notebook.

---

## 5. Encoding Categorical Features

Categorical variables such as **Location** cannot be directly used by most machine learning algorithms.

Therefore, **One-Hot Encoding** is applied to convert categorical values into numerical features.

Scikit-learn's `OneHotEncoder` or `pd.get_dummies()` can be used.

Example:

```python
pd.get_dummies(df, columns=["Location"], drop_first=True)
```

---

## 6. Correlation Analysis

A correlation matrix is created to understand relationships between numerical variables and house prices.

A **Seaborn heatmap** is used to visualize the correlations.

The analysis helps identify which numerical features have stronger positive or negative relationships with the target variable.

```python
import seaborn as sns
import matplotlib.pyplot as plt

plt.figure(figsize=(10, 6))
sns.heatmap(df.corr(numeric_only=True), annot=True, cmap="coolwarm")
plt.title("Correlation Heatmap")
plt.show()
```

---

## 7. Train/Test Split

The dataset is divided into:

* **80% Training Data**
* **20% Testing Data**

The training dataset is used to train the model, while the testing dataset evaluates how well the model performs on unseen data.

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.20, random_state=42
)
```

---

## 8. Linear Regression Model

A **Linear Regression** model is trained using Scikit-learn.

Linear Regression attempts to model the relationship between the input features and house price.

```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()
model.fit(X_train, y_train)

y_pred = model.predict(X_test)
```

The general form of the model is:

**Predicted Price = Intercept + (Coefficient × Feature)**

---

## 9. Model Evaluation

The trained model is evaluated using three important regression metrics.

### Mean Squared Error (MSE)

MSE measures the average squared difference between actual and predicted prices.

A lower MSE indicates better performance.

### Root Mean Squared Error (RMSE)

RMSE is the square root of MSE and represents prediction error in the same unit as the target variable.

A lower RMSE indicates better predictions.

### R² Score

R² measures how much of the variation in house prices is explained by the model.

A higher R² generally indicates better model performance.

Example:

```python
from sklearn.metrics import mean_squared_error, r2_score
import numpy as np

mse = mean_squared_error(y_test, y_pred)
rmse = np.sqrt(mse)
r2 = r2_score(y_test, y_pred)

print("MSE:", mse)
print("RMSE:", rmse)
print("R² Score:", r2)
```

### Model Results

The actual results are generated after running the notebook.

| Metric   | Linear Regression |
| -------- | ----------------: |
| MSE      |    Dataset result |
| RMSE     |    Dataset result |
| R² Score |    Dataset result |

---

## 10. Actual vs Predicted Prices

A scatter plot is created to compare:

* Actual house prices
* Predicted house prices

A diagonal reference line represents ideal predictions.

The closer the points are to this line, the better the model's predictions.

---

## 11. Residual Analysis

Residuals represent the difference between actual and predicted values.

```python
residuals = y_test - y_pred
```

A residual plot is used to check whether the errors are randomly distributed.

A good regression model should ideally show:

* Randomly distributed residuals
* No clear pattern
* No strong funnel shape
* Residuals centered around zero

A systematic pattern may indicate that the linear model is not capturing some important relationship in the data.

---

## 12. Coefficient Analysis

Linear Regression coefficients are analyzed to understand the impact of individual features on house prices.

### Positive Coefficient

A positive coefficient indicates that an increase in that feature is associated with an increase in predicted price, while holding other features constant.

### Negative Coefficient

A negative coefficient indicates that an increase in that feature is associated with a decrease in predicted price, holding other features constant.

The features with the largest positive and negative coefficients are identified in the notebook.

**Important:** Coefficients should be interpreted carefully, especially when features are measured on different scales or when categorical variables have been encoded.

---

# ⭐ Bonus: Ridge Regression

As an optional extension, Linear Regression can be compared with **Ridge Regression**.

Ridge Regression adds regularization to reduce the effect of large coefficients and can help when features are highly correlated.

Example:

```python
from sklearn.linear_model import Ridge

ridge_model = Ridge(alpha=1.0)
ridge_model.fit(X_train, y_train)

ridge_pred = ridge_model.predict(X_test)
```

The performance of Linear Regression and Ridge Regression can then be compared using MSE, RMSE, and R².

| Model             |            MSE |           RMSE |             R² |
| ----------------- | -------------: | -------------: | -------------: |
| Linear Regression | Dataset result | Dataset result | Dataset result |
| Ridge Regression  | Dataset result | Dataset result | Dataset result |

---

# 📈 Visualizations

The project includes the following visualizations:

### 1. House Price Distribution

Shows the distribution of the target variable.

### 2. Correlation Heatmap

Shows relationships between numerical features.

### 3. Actual vs Predicted Prices

Evaluates how closely predictions match actual prices.

### 4. Residual Plot

Helps identify systematic errors in the model.

### 5. Coefficient Analysis

Shows which features have the strongest positive or negative model coefficients.

---

# 💡 Key Insights

The project can provide insights into:

* Which property features are important for predicting prices
* The relationship between property characteristics and price
* How accurately Linear Regression predicts house prices
* Whether prediction errors show systematic patterns
* Which features have the strongest positive or negative coefficients
* Whether regularization improves model performance

The final insights and numerical results are based on the dataset used in the notebook.

---

# 🚀 Real-World Applications

House price prediction models can be useful for:

* Real estate companies
* Property buyers and sellers
* Real estate investment analysis
* Property valuation
* Market analysis
* Financial institutions
* Real estate recommendation systems

---

# 🔑 Skills Demonstrated

* Python
* Pandas
* NumPy
* Exploratory Data Analysis
* Data Cleaning
* Feature Selection
* One-Hot Encoding
* Correlation Analysis
* Linear Regression
* Ridge Regression
* MSE
* RMSE
* R² Score
* Residual Analysis
* Model Interpretation
* Data Visualization
* Machine Learning

---

# 📋 Requirements

Install the required libraries using:

```bash
pip install -r requirements.txt
```

Example `requirements.txt`:

```text
pandas
numpy
scikit-learn
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

This project demonstrates an end-to-end machine learning workflow for predicting house prices using **Linear Regression**.

Starting with data cleaning and exploratory analysis, the project handles missing values, encodes categorical variables, identifies important predictors, trains a regression model, evaluates its performance using MSE, RMSE, and R², and interprets the model coefficients.

The project also includes residual analysis and actual-versus-predicted visualization to assess model performance. As a bonus, Ridge Regression can be used to compare the performance of a regularized model with standard Linear Regression.
