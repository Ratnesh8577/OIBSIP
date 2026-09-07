# Retail Sales Exploratory Data Analysis

## 📌 Project Overview

This project performs a thorough **Exploratory Data Analysis (EDA)** on a retail sales dataset to uncover sales patterns, customer behaviour, product performance, and actionable business insights.

The analysis uses Python-based data analysis and visualization techniques to understand historical sales trends, customer demographics, product performance, and relationships between numerical variables.

---

## 🎯 Objective

Perform a comprehensive Exploratory Data Analysis on a retail sales dataset to:

* Understand the structure and quality of the dataset
* Calculate descriptive statistics
* Analyze monthly and quarterly sales trends
* Study customer demographics
* Identify top-selling products
* Analyze revenue by product category
* Identify relationships between numerical variables
* Discover additional non-obvious business insights
* Provide actionable recommendations based on the findings

---

## 🛠️ Tech Stack

* **Python**
* **Pandas** – Data manipulation and analysis
* **NumPy** – Numerical calculations
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization
* **Jupyter Notebook** – Analysis environment

---

# 📂 Project Structure

```text
DataAnalytics-L1-EDARetailSales/
│
├── Retail_Sales_EDA.ipynb
├── README.md
├── requirements.txt
│
├── dataset/
│   └── retail_sales.csv
│
└── screenshots/
    ├── monthly_sales_trend.png
    ├── quarterly_sales_trend.png
    ├── age_group_distribution.png
    ├── gender_distribution.png
    ├── top_10_products.png
    ├── revenue_by_category.png
    ├── correlation_heatmap.png
    ├── additional_insight.png
    └── key_findings.png
```

---

# 📊 Dataset

The project uses a retail sales dataset containing transaction-level information about customers, products, sales, and revenue.

Depending on the dataset version, important columns may include:

* Transaction ID
* Date
* Customer ID
* Gender
* Age
* Product Category
* Product / Item
* Quantity
* Price per Unit
* Total Amount / Revenue

The dataset is stored in:

```text
dataset/retail_sales.csv
```

---

# 🔍 1. Initial Dataset Inspection

The analysis begins by loading and inspecting the dataset.

The following checks are performed:

* Number of rows and columns
* Column names
* Data types
* Missing values
* Duplicate records
* Basic dataset information

Example:

```python
df.shape
df.info()
df.isnull().sum()
df.duplicated().sum()
```

This step helps identify potential data-quality issues before performing further analysis.

---

# 📈 2. Descriptive Statistics

Descriptive statistics are calculated for all relevant numerical variables.

The analysis includes:

* **Mean**
* **Median**
* **Mode**
* **Standard deviation**
* Minimum
* Maximum
* Quartiles

Example:

```python
df.describe()
```

These statistics help understand the central tendency and spread of sales-related variables.

---

# 📅 3. Time Series Analysis

Sales trends are analyzed over time to identify changes in business performance.

The date column is converted into an appropriate datetime format before extracting:

* Year
* Month
* Quarter

---

## Monthly Sales Trend

Monthly sales are aggregated and displayed using a line chart.

This visualization helps identify:

* Increasing or decreasing sales
* Seasonal patterns
* High-performing months
* Low-performing months

The notebook includes written observations below the chart.

---

## Quarterly Sales Trend

Sales are also grouped by quarter to identify broader business trends.

The quarterly analysis helps management understand performance across larger time periods and identify potential seasonal effects.

---

# 👥 4. Customer Demographics Analysis

Customer demographics are analyzed to understand who contributes to the sales.

---

## Age Group Analysis

Customers are divided into meaningful age groups.

For example:

```text
18–25
26–35
36–45
46–55
56+
```

The distribution is visualized to identify the major customer segments.

The analysis can help businesses understand which age groups represent the largest customer base.

---

## Gender Analysis

The gender distribution of customers is visualized using a bar chart.

This helps identify differences in customer representation and can support targeted marketing strategies.

---

# 🛍️ 5. Product Analysis

Product performance is analyzed to identify the products generating the highest sales.

---

## Top 10 Best-Selling Products

The top 10 products are identified based on an appropriate sales measure such as:

* Quantity sold
* Number of transactions
* Revenue

A bar chart is used to visualize the top-performing products.

This helps identify products that may require:

* Higher inventory levels
* Promotional campaigns
* Better placement
* Additional product variations

---

# 💰 6. Revenue by Product Category

Revenue is aggregated by product category.

A bar chart is created to compare category-level revenue.

This analysis identifies:

* Highest-revenue categories
* Lowest-revenue categories
* Categories with significant business contribution

Understanding category performance can help businesses allocate inventory and marketing budgets more effectively.

---

# 🔥 7. Correlation Analysis

A correlation matrix is created for numerical variables.

Example:

```python
correlation_matrix = df.corr(numeric_only=True)
```

The correlation matrix is visualized using a Seaborn heatmap.

The analysis helps identify relationships between variables such as:

* Age
* Quantity
* Price
* Revenue / Total Amount

Strong positive or negative correlations are investigated further.

**Note:** Correlation indicates association between variables and does not by itself prove causation.

---

# 💡 8. Additional Business Insight

At least one additional visualization is created to identify a **non-obvious pattern** in the dataset.

Possible analyses include:

* Average transaction value by age group
* Revenue by gender and product category
* Monthly sales by product category
* Quantity vs. revenue
* Customer spending behaviour
* Average purchase value by customer segment

The selected visualization is accompanied by a written observation explaining the discovered pattern.

---

# 📝 9. Observations

Markdown cells are included throughout the notebook after major visualizations.

Each observation explains:

* What the chart shows
* The most important pattern
* Why the pattern matters
* Possible business implications

This ensures that the project does not only present charts but also translates the analysis into meaningful insights.

---

# 📊 Analysis Summary

| Analysis               | Visualization        |
| ---------------------- | -------------------- |
| Dataset Inspection     | Tables / Summary     |
| Descriptive Statistics | Statistical Table    |
| Monthly Sales          | Line Chart           |
| Quarterly Sales        | Line Chart           |
| Age Groups             | Bar Chart            |
| Gender Distribution    | Bar Chart            |
| Top 10 Products        | Bar Chart            |
| Revenue by Category    | Bar Chart            |
| Numerical Correlations | Heatmap              |
| Additional Insight     | Custom Visualization |

---

# 🚀 Business Recommendations

The final recommendations should be based on the actual results obtained from the dataset.

### 1. Focus on High-Performing Products

Maintain sufficient inventory and promote products that consistently generate high sales or revenue.

### 2. Target Key Customer Segments

Use age and gender analysis to identify the most valuable customer groups and create targeted marketing campaigns.

### 3. Optimize Seasonal Planning

Use monthly and quarterly sales trends to anticipate periods of high and low demand and adjust inventory accordingly.

### 4. Invest in High-Revenue Categories

Allocate marketing and inventory resources toward categories that contribute significantly to overall revenue.

### 5. Improve Underperforming Areas

Investigate products or categories with consistently low performance and consider promotional offers, pricing adjustments, or product strategy changes.

---

# 📌 Key Skills Demonstrated

* Exploratory Data Analysis
* Data Cleaning
* Data Preprocessing
* Descriptive Statistics
* Time Series Analysis
* Customer Segmentation
* Demographic Analysis
* Product Performance Analysis
* Revenue Analysis
* Correlation Analysis
* Data Visualization
* Business Insight Generation
* Data-driven Decision Making

---

# 📋 Requirements

Install the required Python libraries using:

```bash
pip install -r requirements.txt
```

### `requirements.txt`

```text
pandas
numpy
matplotlib
seaborn
jupyter
```

---

# ▶️ How to Run the Project

### 1. Clone the repository

```bash
git clone <your-github-repository-url>
```

### 2. Navigate to the project folder

```bash
cd OIBSIP/DataAnalytics-L1-EDARetailSales
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

### 5. Open the notebook

```text
Retail_Sales_EDA.ipynb
```

### 6. Run all cells

Execute the notebook from beginning to end to reproduce the complete analysis and visualizations.

---

# 📸 Project Screenshots

The `screenshots/` directory contains the major visualizations generated during the analysis:

* Monthly sales trend
* Quarterly sales trend
* Age-group distribution
* Gender distribution
* Top 10 products
* Revenue by category
* Correlation heatmap
* Additional business insight
* Key findings

---

# 🎓 Learning Outcomes

This project demonstrates how raw retail transaction data can be transformed into meaningful business information through:

* Data inspection
* Statistical analysis
* Visualization
* Pattern identification
* Customer behaviour analysis
* Product analysis
* Business interpretation

The project also demonstrates the importance of combining **technical analysis with business reasoning** when working with real-world datasets.

---

# 👨‍💻 Author

**Ratnesh Chauhan**

**OIBSIP – Data Analytics Internship**

---

# 📝 Conclusion

This Exploratory Data Analysis provides a detailed understanding of retail sales performance, customer demographics, product behaviour, and revenue patterns.

By analyzing sales trends, customer segments, product performance, and numerical relationships, businesses can identify opportunities to improve inventory planning, marketing strategies, product selection, and customer engagement.

The final recommendations are derived from the actual patterns identified during the analysis, making the project a practical example of **data-driven business decision-making**.

