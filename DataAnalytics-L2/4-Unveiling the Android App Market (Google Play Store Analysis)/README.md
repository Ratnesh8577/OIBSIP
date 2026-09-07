# Google Play Store Data Analysis

## 📌 Project Overview

This project performs a comprehensive analysis of the **Google Play Store ecosystem** using real-world app and user review data.

The analysis covers data cleaning, exploratory data analysis, app categories, ratings, installs, size, pricing, estimated revenue, and sentiment analysis of user reviews.

The project aims to identify meaningful patterns and provide **data-driven insights for developers planning to launch a new application**.

---

## 🎯 Objective

Perform comprehensive data analysis of the Google Play Store ecosystem by:

* Cleaning messy real-world app data
* Exploring app categories and market saturation
* Analyzing ratings and pricing trends
* Studying app size and installation patterns
* Estimating revenue from paid applications
* Performing sentiment analysis on user reviews
* Identifying actionable insights for app developers

---

## 🛠️ Tech Stack

* **Python**
* **Pandas** – Data manipulation and analysis
* **NumPy** – Numerical operations
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization
* **TextBlob / VADER** – Sentiment analysis
* **Plotly** – Interactive visualization
* **Jupyter Notebook** – Development environment

---

# 📂 Project Structure

```text
DataAnalytics-L2-GooglePlayStoreAnalysis/
│
├── Google_Play_Store_Analysis.ipynb
├── README.md
├── requirements.txt
│
├── dataset/
│   ├── googleplaystore.csv
│   └── googleplaystore_user_reviews.csv
│
└── screenshots/
    ├── category_distribution.png
    ├── rating_distribution.png
    ├── average_rating_category.png
    ├── size_vs_installs.png
    ├── paid_free_distribution.png
    ├── paid_price_distribution.png
    ├── revenue_by_category.png
    ├── sentiment_distribution.png
    ├── sentiment_by_category.png
    └── interactive_visual.html
```

---

# 📊 Datasets

Two datasets are used separately in this project.

### 1. Google Play Store Apps Dataset

Contains information about applications, including:

* App name
* Category
* Rating
* Reviews
* Size
* Installs
* Type
* Price
* Content Rating
* Genres

### 2. User Reviews Dataset

Contains user feedback and sentiment-related information for applications.

Important columns may include:

* App
* Translated_Review
* Sentiment
* Sentiment_Polarity
* Sentiment_Subjectivity

The exact columns depend on the dataset version used.

---

# 🧹 1. Data Cleaning

The Play Store dataset contains several real-world data quality issues.

The cleaning process includes:

* Handling missing values
* Removing duplicate applications
* Correcting data types
* Cleaning numerical columns
* Standardizing text values
* Handling invalid records

---

## Cleaning the Installs Column

The `Installs` column may contain values such as:

```text
1,000+
10,000+
100,000+
1,000,000+
```

These values are converted from strings into numerical values by removing commas and the `+` symbol.

Example:

```text
"10,000+" → 10000
```

This allows the column to be used for numerical analysis.

---

## Cleaning the Price Column

The `Price` column may contain values such as:

```text
$4.99
$9.99
$0
```

The `$` symbol is removed and the values are converted into numerical format.

---

## Handling Missing Values

Missing values are identified using:

```python
df.isnull().sum()
```

Appropriate strategies are applied depending on the column, such as:

* Median imputation
* Mode imputation
* Removing records
* Retaining missing values where appropriate

The cleaning decisions are documented in the notebook.

---

## Removing Duplicates

Duplicate app records are identified and removed to prevent duplicated applications from affecting the analysis.

```python
df.duplicated().sum()
```

---

# 📱 2. Category Analysis

The distribution of applications across different categories is analyzed.

A bar chart is created to identify:

* Most common app categories
* Least represented categories
* Potentially saturated categories

Categories with a very large number of applications may indicate a highly competitive or saturated market.

---

# ⭐ 3. Ratings Analysis

The distribution of application ratings is analyzed to understand overall app quality.

A rating distribution visualization is created to identify:

* Common rating ranges
* Average rating patterns
* Extremely high or low ratings
* Possible outliers

---

## Average Rating by Category

The average rating for each app category is calculated and visualized.

This helps identify categories where applications generally receive:

* Higher ratings
* Lower ratings
* More consistent user satisfaction

---

# 📦 4. Size and Installs Analysis

The relationship between application size and number of installs is explored using a scatter plot.

The analysis investigates whether larger or smaller applications tend to receive more installations.

The relationship is evaluated using:

* Scatter plots
* Correlation analysis
* Trend interpretation

Correlation does not necessarily imply causation, so the results are interpreted carefully.

---

# 💰 5. Pricing Analysis

Applications are divided into:

* **Free**
* **Paid**

A bar chart is used to compare the number of free and paid applications.

---

## Paid App Price Distribution

For paid applications, the distribution of prices is analyzed to identify:

* Common price ranges
* Most expensive applications
* Typical pricing patterns

This provides insight into how developers price paid applications on the Play Store.

---

# 💵 6. Revenue Estimation

Estimated revenue is calculated for paid applications.

A simplified revenue estimate can be calculated as:

```text
Estimated Revenue = Price × Installs
```

This provides an approximate estimate of potential gross revenue based on the available Play Store data.

**Note:** This is only an estimate and does not account for factors such as refunds, taxes, platform fees, promotional pricing, or actual paid conversions.

Revenue is aggregated by category to identify categories with potentially higher estimated revenue.

---

# 💬 7. User Review Sentiment Analysis

User reviews are analyzed using **TextBlob** or **VADER**.

Reviews are classified into:

* **Positive**
* **Negative**
* **Neutral**

The sentiment analysis helps understand how users feel about applications.

---

## TextBlob Sentiment

TextBlob can provide:

* **Polarity** – Measures whether the sentiment is positive or negative
* **Subjectivity** – Measures whether the text is more factual or opinion-based

A simplified classification can be applied based on polarity.

For example:

```text
Polarity > 0     → Positive
Polarity < 0     → Negative
Polarity = 0     → Neutral
```

The exact thresholding method is documented in the notebook.

---

# 📊 8. Sentiment Distribution

The overall distribution of:

* Positive reviews
* Negative reviews
* Neutral reviews

is visualized using a bar chart.

This provides a high-level understanding of user satisfaction across the analyzed reviews.

---

# 🏷️ 9. Sentiment by Category

User reviews are connected with app categories using the application name.

The analysis determines which categories have:

* Highest positive sentiment
* Highest negative sentiment
* More balanced sentiment

This helps developers understand user satisfaction patterns within different app markets.

---

# 📈 10. Interactive Visualization

At least one interactive visualization is created using **Plotly**.

Possible interactive visualizations include:

* Category vs. installs
* Rating vs. reviews
* Price vs. installs
* Category vs. average rating
* App size vs. installs

Plotly allows users to hover over data points and explore individual values interactively.

Example:

```python
import plotly.express as px

fig = px.scatter(
    df,
    x="Reviews",
    y="Rating",
    size="Installs",
    hover_name="App",
    title="Reviews vs Rating"
)

fig.show()
```

---

# 📊 Key Analysis Areas

| Analysis                      | Visualization     |
| ----------------------------- | ----------------- |
| App Category Distribution     | Bar Chart         |
| Rating Distribution           | Histogram         |
| Average Rating by Category    | Bar Chart         |
| Size vs Installs              | Scatter Plot      |
| Free vs Paid Apps             | Bar Chart         |
| Paid App Prices               | Distribution Plot |
| Estimated Revenue by Category | Bar Chart         |
| Review Sentiment              | Bar Chart         |
| Sentiment by Category         | Bar Chart         |
| Interactive Analysis          | Plotly            |

---

# 💡 Developer Insights

The analysis is designed to provide at least three data-driven insights for developers.

### Insight 1 — Market Competition

Identify categories with a large number of existing applications to understand market saturation and competition.

### Insight 2 — User Satisfaction

Compare average ratings and review sentiment across categories to identify areas where users are more or less satisfied.

### Insight 3 — Monetization Strategy

Analyze free vs. paid applications, pricing patterns, installs, and estimated revenue to understand potential monetization opportunities.

The final insights should be based on the actual results generated from the dataset.

---

# 🚀 Recommendations for a New App Developer

Based on the analysis, developers should consider:

1. **Choose a category carefully** by balancing market demand with competition.
2. **Focus on user experience** because ratings and reviews can strongly influence an application's reputation.
3. **Use data-driven pricing** when deciding whether an application should be free or paid.
4. **Monitor user sentiment** to identify common complaints and areas for improvement.
5. **Optimize application performance and size** while maintaining useful functionality.
6. **Study successful applications** in the target category before launching a new product.

---

# 🔑 Skills Demonstrated

* Python
* Pandas
* NumPy
* Data Cleaning
* Exploratory Data Analysis
* Data Visualization
* Category Analysis
* Rating Analysis
* Pricing Analysis
* Install Analysis
* Revenue Estimation
* Sentiment Analysis
* TextBlob / VADER
* Plotly
* Statistical Analysis
* Business Insight Generation

---

# 📋 Requirements

Install the required libraries using:

```bash
pip install -r requirements.txt
```

### `requirements.txt`

```text
pandas
numpy
matplotlib
seaborn
textblob
plotly
jupyter
```

If VADER is used instead of TextBlob, include:

```text
nltk
```

---

# 📸 Project Screenshots

The project includes visualizations covering:

* App category distribution
* Rating distribution
* Average rating by category
* Size vs. installs
* Free vs. paid applications
* Paid app price distribution
* Estimated revenue by category
* Sentiment distribution
* Sentiment by category
* Interactive Plotly visualization

---

# 👨‍💻 Author

**Ratnesh Chauhan**

**OIBSIP – Data Analytics Internship**

---

# 📝 Conclusion

This project provides a comprehensive analysis of the Google Play Store ecosystem using app metadata and user reviews.

Through data cleaning and exploratory analysis, the project investigates application categories, ratings, installs, size, pricing, and estimated revenue. Sentiment analysis of user reviews provides additional insight into user satisfaction and category-level sentiment.

The combination of statistical analysis, visualization, and sentiment analysis demonstrates how real-world app marketplace data can be transformed into actionable business insights.

The final findings can help developers make more informed decisions about **app category selection, pricing, user experience, and product strategy**.
