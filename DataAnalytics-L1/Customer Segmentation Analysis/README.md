# Customer Segmentation Using K-Means Clustering

## 📌 Project Overview

This project focuses on segmenting an e-commerce company's customer base into distinct groups based on their purchasing behaviour.

The project uses **RFM (Recency, Frequency, Monetary) analysis** and the **K-Means clustering algorithm** to identify customers with similar purchasing patterns. These segments can help businesses develop targeted marketing strategies, improve customer retention, and increase customer lifetime value.

---

## 🎯 Objective

Apply clustering algorithms to segment an e-commerce company's customer base into distinct groups based on purchasing behaviour, enabling targeted and data-driven marketing strategies.

---

## 🛠️ Tech Stack

* **Python**
* **Pandas** – Data manipulation and analysis
* **NumPy** – Numerical computations
* **Scikit-learn** – StandardScaler and K-Means clustering
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization
* **Jupyter Notebook** – Development environment

---

## 📊 Project Methodology

### 1. Dataset Loading and Inspection

The dataset is loaded using Pandas and inspected for:

* Dataset shape
* Column names
* Data types
* Missing values
* Duplicate records
* Inconsistent data

### 2. Data Cleaning

Data-quality issues are handled before performing customer segmentation. This includes managing missing values, duplicate records, incorrect data types, and inconsistent values where required.

### 3. Descriptive Statistics

Customer purchasing behaviour is analyzed using:

* Average purchase value
* Purchase frequency
* Customer lifetime value (CLV), where available
* Other relevant numerical statistics

### 4. RFM Analysis

Three key behavioural features are considered:

**Recency:** Number of days since the customer's most recent purchase.

**Frequency:** Number of purchases/orders made by the customer.

**Monetary:** Total amount spent by the customer.

These features provide a useful representation of customer purchasing behaviour.

### 5. Feature Selection

Two to three important behavioural features are selected for clustering, primarily:

```text
Recency
Frequency
Monetary
```

### 6. Feature Standardisation

Since the selected features can have different numerical scales, `StandardScaler` from Scikit-learn is used to standardize the features before clustering.

### 7. Elbow Method

The Elbow Method is used to evaluate different values of K and identify an appropriate number of customer clusters.

### 8. K-Means Clustering

The selected optimal K value is used with the K-Means algorithm to group customers according to similar purchasing behaviour.

### 9. Cluster Visualization

The resulting clusters are visualized using scatter plots, including combinations such as:

* Recency vs Frequency
* Frequency vs Monetary

### 10. Cluster Profiling

Each cluster is analyzed by calculating the mean values of the RFM features. This helps understand the characteristics and purchasing behaviour of each customer group.

### 11. Cluster Size Analysis

A bar chart is used to show the number of customers belonging to each cluster.

---

## 📈 Visualizations

The project includes the following visualizations:

* Elbow Method plot
* Recency vs Frequency cluster scatter plot
* Frequency vs Monetary cluster scatter plot
* Customers per cluster bar chart
* Cluster profile analysis

---

## 👥 Customer Segmentation

Based on the resulting RFM characteristics, clusters can be interpreted into customer types such as:

| Customer Type        | Typical Characteristics                    | Recommended Action                        |
| -------------------- | ------------------------------------------ | ----------------------------------------- |
| High-Value Customers | Low recency, high frequency, high spending | VIP rewards and loyalty benefits          |
| Loyal Customers      | Frequent purchases and consistent spending | Personalized recommendations              |
| Potential Customers  | Moderate engagement and spending           | Offers to increase purchase frequency     |
| At-Risk Customers    | High recency and declining activity        | Re-engagement campaigns                   |
| Low-Value Customers  | Low frequency and low spending             | Targeted discounts and promotional offers |

**Note:** The actual customer segment names and characteristics are determined from the clustering results and may vary depending on the dataset.

---

## 💡 Marketing Recommendations

### 1. High-Value Customers

Provide exclusive offers, VIP benefits, loyalty rewards, and early access to new products.

### 2. Loyal Customers

Use personalized product recommendations, loyalty points, and repeat-purchase incentives.

### 3. Potential Customers

Provide limited-time discounts, product bundles, and personalized promotions to encourage more frequent purchases.

### 4. At-Risk Customers

Launch targeted re-engagement campaigns through email, notifications, or special offers.

### 5. Low-Value Customers

Use cost-effective promotional campaigns and discounts to increase engagement while controlling marketing costs.

---

## 📁 Project Structure

```text
DataAnalytics-L1-CustomerSegmentation/
│
├── Customer_Segmentation.ipynb
├── README.md
├── requirements.txt
│
├── dataset/
│   └── ecommerce_customers.csv
│
└── screenshots/
    ├── elbow_method.png
    ├── cluster_recency_frequency.png
    ├── cluster_frequency_monetary.png
    ├── customers_per_cluster.png
    └── cluster_profile.png
```

---

## 🔑 Key Skills Demonstrated

* Data Cleaning
* Exploratory Data Analysis
* RFM Analysis
* Feature Engineering
* Feature Standardisation
* K-Means Clustering
* Elbow Method
* Customer Segmentation
* Data Visualization
* Business Insight Generation
* Marketing Strategy Development

---

## 🚀 Expected Business Impact

Customer segmentation allows an e-commerce business to move from a one-size-fits-all marketing approach toward more personalized strategies.

Understanding customer purchasing behaviour can help the business:

* Improve customer retention
* Increase repeat purchases
* Identify high-value customers
* Re-engage inactive customers
* Improve marketing campaign effectiveness
* Allocate marketing resources more efficiently

---

## 👨‍💻 Author

**Ratnesh Chauhan**

**OIBSIP – Data Analytics Internship**

---

## 📝 Conclusion

K-Means clustering combined with RFM analysis provides a practical approach for identifying meaningful customer segments. By understanding differences in recency, purchase frequency, and monetary value, an e-commerce company can create targeted marketing strategies for different customer groups and make more informed business decisions.
