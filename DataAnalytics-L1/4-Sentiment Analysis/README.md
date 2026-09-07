# Sentiment Analysis of Text Data

## 📌 Project Overview

This project focuses on building a machine learning system to classify text data into three sentiment categories:

* **Positive**
* **Negative**
* **Neutral**

The project applies Natural Language Processing (NLP) techniques to preprocess text, extract meaningful features using **TF-IDF**, and train machine learning classification models.

The goal is to understand public opinion or customer feedback and provide useful insights that can support real-world business decisions.

---

## 🎯 Objective

Build a machine learning model that classifies the sentiment of text data as positive, negative, or neutral, providing insights into public opinion and customer feedback.

---

## 🛠️ Tech Stack

* **Python**
* **Pandas** – Data loading and manipulation
* **NumPy** – Numerical operations
* **Scikit-learn** – Machine learning and TF-IDF
* **NLTK / TextBlob** – Natural Language Processing
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization
* **WordCloud** – Sentiment word visualization
* **Jupyter Notebook** – Development environment

---

## 📂 Project Structure

```text
DataAnalytics-L1-SentimentAnalysis/
│
├── Sentiment_Analysis.ipynb
├── README.md
├── requirements.txt
│
├── dataset/
│   └── sentiment_dataset.csv
│
└── screenshots/
    ├── sentiment_distribution.png
    ├── model_comparison.png
    ├── confusion_matrix_nb.png
    ├── confusion_matrix_lr.png
    ├── wordcloud_positive.png
    ├── wordcloud_negative.png
    └── wordcloud_neutral.png
```

---

## 🔍 Project Workflow

### 1. Dataset Loading and Inspection

The sentiment dataset is loaded using Pandas and inspected to understand:

* Dataset shape
* Column names
* Data types
* Missing values
* Sentiment class distribution
* Duplicate records

The number of positive, negative, and neutral records is analyzed to understand the balance of the dataset.

---

## 🧹 2. Text Preprocessing

Raw text is cleaned and prepared for machine learning using an NLP preprocessing pipeline.

The preprocessing steps include:

1. Convert text to lowercase
2. Remove punctuation
3. Tokenize the text
4. Remove stopwords
5. Apply stemming or lemmatization where appropriate

Example:

```text
Original:
"I absolutely LOVE this product!"

Processed:
"absolutely love product"
```

---

## 📊 3. Sentiment Distribution

A bar chart is created to visualize the number of:

* Positive reviews
* Negative reviews
* Neutral reviews

This helps identify whether the dataset is balanced across sentiment categories.

---

## 🧮 4. TF-IDF Feature Extraction

**TF-IDF (Term Frequency–Inverse Document Frequency)** converts text into numerical features that machine learning algorithms can process.

TF-IDF gives higher importance to words that are frequent in a particular document but less common across the entire dataset.

It helps identify words that are more informative for distinguishing between different sentiment classes.

The project uses:

```python
from sklearn.feature_extraction.text import TfidfVectorizer
```

---

## ✂️ 5. Train/Test Split

The dataset is divided into:

* **80% Training Data**
* **20% Testing Data**

The training data is used to train the machine learning models, while the testing data is used to evaluate their performance on unseen text.

---

## 🤖 6. Machine Learning Models

Two classification algorithms are trained and compared.

### Model 1 — Naive Bayes

Multinomial Naive Bayes is suitable for text classification problems because it works effectively with word-frequency and TF-IDF features.

### Model 2 — Logistic Regression

Logistic Regression is used as a second classification model to compare its performance with Naive Bayes.

---

## 📈 7. Model Evaluation

Both models are evaluated using:

* Accuracy
* Precision
* Recall
* F1-score
* Confusion Matrix

A model comparison is performed to determine which classifier provides better sentiment classification performance.

The actual performance values are generated from the dataset and displayed in the notebook.

---

## 🔲 8. Confusion Matrix

Confusion matrices are created for both models to identify:

* Correctly classified Positive samples
* Correctly classified Negative samples
* Correctly classified Neutral samples
* Misclassified samples

This provides a detailed view of the strengths and weaknesses of each classifier.

---

## ☁️ 9. WordCloud Analysis

WordClouds are generated separately for each sentiment category:

* Positive sentiment
* Negative sentiment
* Neutral sentiment

These visualizations highlight commonly occurring words within each sentiment class.

---

## ❌ 10. Error Analysis

Five incorrectly classified examples are selected from the test dataset.

Each misclassification is reviewed to understand possible causes, such as:

* Sarcasm
* Ambiguous language
* Context-dependent expressions
* Negation
* Short or unclear text
* Words with multiple meanings

This analysis helps identify areas where the model could be improved.

---

## 📊 Model Comparison

The performance of Naive Bayes and Logistic Regression is compared using their evaluation metrics.

| Model               |       Accuracy |      Precision |         Recall |       F1-Score |
| ------------------- | -------------: | -------------: | -------------: | -------------: |
| Naive Bayes         | Dataset result | Dataset result | Dataset result | Dataset result |
| Logistic Regression | Dataset result | Dataset result | Dataset result | Dataset result |

The model with the strongest overall performance is selected as the preferred classifier.

---

## 💡 Key Insights

The project helps identify:

* Overall sentiment distribution
* Common words associated with each sentiment
* Differences in classifier performance
* Common types of classification errors
* Patterns in customer or public feedback

The exact insights are derived from the dataset and model results.

---

## 🚀 Real-World Applications

Sentiment analysis can be used in many practical applications, including:

### Customer Feedback Analysis

Businesses can automatically analyze customer reviews and identify satisfaction levels.

### Social Media Monitoring

Organizations can monitor public sentiment toward products, services, or campaigns.

### Product Reviews

E-commerce companies can analyze large numbers of product reviews automatically.

### Brand Monitoring

Companies can track positive and negative opinions about their brand.

### Customer Support

Support teams can prioritize negative feedback and identify dissatisfied customers.

---

## 📈 Possible Future Improvements

The project could be improved by:

* Using advanced NLP models such as BERT
* Increasing the size and diversity of the dataset
* Hyperparameter tuning
* Handling class imbalance
* Using word embeddings
* Improving sarcasm and context detection
* Applying cross-validation

---

## 🔑 Skills Demonstrated

* Natural Language Processing
* Text Preprocessing
* Tokenization
* Stopword Removal
* TF-IDF
* Machine Learning Classification
* Naive Bayes
* Logistic Regression
* Model Evaluation
* Confusion Matrix
* Error Analysis
* Data Visualization
* WordCloud
* Python and Pandas

---

## 📁 Project Files

* `Sentiment_Analysis.ipynb` – Complete NLP and machine learning analysis
* `dataset/` – Dataset used for the project
* `screenshots/` – Important project visualizations
* `requirements.txt` – Required Python libraries
* `README.md` – Project documentation

---

## 👨‍💻 Author

**Ratnesh Chauhan**

**OIBSIP – Data Analytics Internship**

---

## 📝 Conclusion

This project demonstrates how Natural Language Processing and machine learning can be used to classify text into positive, negative, and neutral sentiment categories.

By comparing Naive Bayes and Logistic Regression, the project identifies an effective model for sentiment classification. The resulting system can help businesses analyze large volumes of customer feedback and public opinion, enabling faster and more data-driven decision-making.
