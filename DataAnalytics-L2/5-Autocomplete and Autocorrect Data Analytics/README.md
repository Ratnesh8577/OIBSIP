# NLP Autocomplete and Autocorrect System

## 📌 Project Overview

This project focuses on analyzing the **efficiency and accuracy of autocomplete and autocorrect algorithms** using Natural Language Processing (NLP) techniques.

The project implements multiple approaches for:

* Predicting the next word from a given text prefix
* Correcting deliberately misspelled words
* Measuring prediction and correction performance
* Comparing different NLP algorithms
* Visualizing word frequencies and autocorrect performance

The objective is to understand how basic NLP techniques can be used to build text prediction and spelling correction systems.

---

## 🎯 Objective

Analyse the efficiency and accuracy of autocomplete and autocorrect algorithms using NLP techniques.

The project implements and compares multiple approaches for **text prediction and spelling correction** using a real-world text corpus.

---

## 🛠️ Tech Stack

* **Python**
* **Pandas** – Data manipulation and analysis
* **NLTK** – Natural Language Processing
* **PySpellChecker** – Spelling correction
* **Collections** – Frequency-based language modeling
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization
* **Jupyter Notebook** – Development environment

---

# 📂 Project Structure

```text
DataAnalytics-L2-AutocompleteAutocorrect/
│
├── NLP_Autocomplete_Autocorrect.ipynb
├── README.md
├── requirements.txt
│
├── dataset/
│   └── text_corpus.txt
│
└── screenshots/
    ├── top_20_words.png
    ├── autocomplete_predictions.png
    ├── autocorrect_results.png
    ├── confusion_matrix.png
    ├── algorithm_comparison.png
    └── performance_metrics.png
```

---

# 📚 1. Text Corpus

A large real-world text corpus is used to train and evaluate the NLP models.

The corpus is used to:

* Build the vocabulary
* Calculate word frequencies
* Generate n-grams
* Train autocomplete models
* Test spelling correction

The dataset is stored in:

```text
dataset/text_corpus.txt
```

The selected corpus should contain sufficiently large and diverse English text to provide meaningful word and n-gram frequencies.

---

# 🧹 2. NLP Preprocessing

Before building the models, the raw text is cleaned and transformed.

The preprocessing pipeline includes:

### Tokenization

The text is divided into individual words/tokens.

```python
tokens = nltk.word_tokenize(text)
```

### Lowercasing

All words are converted to lowercase to avoid treating words such as:

```text
Python
python
PYTHON
```

as different tokens.

### Punctuation Removal

Punctuation marks are removed to improve the quality of the vocabulary and n-gram model.

### Stopword Removal

Common English stopwords are removed using NLTK.

Examples:

```text
the
is
a
an
of
to
```

The preprocessing steps are documented and implemented in the Jupyter Notebook.

---

# 📊 3. Word Frequency Analysis

Word frequencies are calculated using Python's `collections.Counter`.

Example:

```python
from collections import Counter

word_frequency = Counter(tokens)
```

The **20 most frequent words** are visualized using a bar chart.

This provides an overview of the most commonly occurring words in the corpus.

---

# ⌨️ 4. Autocomplete System

The autocomplete system predicts the next word based on previously observed words.

A **frequency-based n-gram language model** is implemented.

Two approaches are compared:

### Approach 1 — Bigram Model

A bigram consists of two consecutive words.

Example:

```text
machine learning
```

If the user enters:

```text
machine
```

the model searches for words that frequently occur after `machine`.

---

### Approach 2 — Trigram Model

A trigram consists of three consecutive words.

Example:

```text
machine learning model
```

The model uses the previous two words to predict the next word.

For example:

```text
machine learning →
```

may generate predictions such as:

```text
model
algorithms
techniques
```

depending on the corpus.

---

# 🔍 Autocomplete Testing

Autocomplete is tested using at least **10 different input prefixes/contexts**.

For each input, the system displays the **Top 3 predicted words**.

Example format:

| Input Prefix | Prediction 1 | Prediction 2 | Prediction 3 |
| ------------ | ------------ | ------------ | ------------ |
| machine      | learning     | translation  | vision       |
| natural      | language     | selection    | resources    |
| data         | analysis     | science      | processing   |

The actual predictions depend on the selected corpus and generated n-gram frequencies.

---

# ✏️ 5. Autocorrect System

The autocorrect component identifies misspelled words and suggests the most appropriate correction.

The implementation uses **edit-distance-based spelling correction**.

`PySpellChecker` is used to:

* Identify potentially misspelled words
* Search for candidate corrections
* Select the most likely correction

Example:

```text
Original → Corrected

recieve → receive
becuase → because
teh → the
adress → address
```

---

# 🔤 6. Edit Distance

Edit distance measures how many operations are required to transform one word into another.

Typical operations include:

* Insertion
* Deletion
* Substitution

For example:

```text
cat → cut
```

requires one substitution:

```text
a → u
```

Therefore, the edit distance is:

```text
1
```

Edit distance helps the autocorrect system identify words that are similar to the misspelled input.

---

# 🧪 7. Autocorrect Testing

At least **20 deliberately misspelled words** are used to evaluate the autocorrect system.

The test records:

* Misspelled word
* Expected correct word
* Predicted correction
* Whether the correction was correct

Example:

| Misspelled | Expected   | Predicted  | Result  |
| ---------- | ---------- | ---------- | ------- |
| recieve    | receive    | receive    | Correct |
| seperate   | separate   | separate   | Correct |
| adress     | address    | address    | Correct |
| definately | definitely | definitely | Correct |

The final accuracy is calculated from the complete test set.

---

# 📏 8. Performance Metrics

Performance is evaluated using appropriate classification and retrieval metrics.

## Autocomplete Precision

Precision measures how many of the returned predictions are relevant/correct.

```text
Precision =
Correct Predictions / Total Predictions
```

---

## Autocomplete Recall

Recall measures how many relevant next-word possibilities were successfully retrieved.

```text
Recall =
Correct Predictions / Total Relevant Predictions
```

Because autocomplete can return multiple valid next words, the evaluation methodology and relevance criteria are clearly defined in the notebook.

---

## Autocorrect Accuracy

Autocorrect accuracy measures the percentage of misspelled words that were corrected correctly.

```text
Accuracy =
Correct Corrections / Total Misspelled Words × 100
```

---

## Autocorrect Precision and Recall

Precision and recall are also calculated by treating the correction task as a prediction problem.

The exact evaluation depends on the predefined expected correction for each test word.

---

# ⚖️ 9. Algorithm Comparison

Two approaches are compared for autocomplete:

### Bigram vs. Trigram

| Feature                | Bigram        | Trigram            |
| ---------------------- | ------------- | ------------------ |
| Context                | Previous word | Previous two words |
| Complexity             | Lower         | Higher             |
| Context awareness      | Limited       | Better             |
| Data requirement       | Lower         | Higher             |
| Prediction specificity | Lower         | Higher             |

The results are compared using:

* Precision
* Recall
* Prediction quality
* Computational requirements

---

# 📈 10. Visualizations

The project contains multiple visualizations.

### Top 20 Most Frequent Words

A bar chart showing the most frequently occurring words in the corpus.

### Autocomplete Predictions

A visualization/table showing the Top 3 predictions for the tested inputs.

### Autocorrect Results

A comparison of expected and predicted corrections.

### Confusion Matrix

A confusion matrix is used to visualize correct and incorrect autocorrect predictions.

### Algorithm Comparison

Performance of different approaches is compared using charts.

### Performance Metrics

Precision, recall, and accuracy are visualized for easier comparison.

---

# 🧮 11. Confusion Matrix

The autocorrect results are evaluated using a confusion matrix or equivalent correct/incorrect outcome visualization.

The matrix helps identify:

* Correctly corrected words
* Incorrect corrections
* Failed corrections
* Common error patterns

This provides a visual representation of autocorrect performance.

---

# 💡 12. Key Insights

The analysis is designed to identify insights such as:

1. **Trigram models can provide more contextual predictions** than bigram models when sufficient training data is available.
2. **Frequency-based autocomplete depends heavily on the training corpus**, meaning uncommon words may receive poor predictions.
3. **Edit-distance-based autocorrection performs well for simple spelling mistakes**, but may struggle with context-dependent corrections.
4. Larger and more diverse corpora can improve vocabulary coverage and prediction quality.
5. A single correct spelling may not always be the correct word in a particular sentence.

The final numerical results should be updated based on the actual notebook execution.

---

# ⚠️ 13. Limitations

This implementation is a simplified NLP system and has several limitations compared with production systems such as **Google Keyboard**.

### Limited Context

Basic n-gram models use only a small amount of previous context and may fail to understand the complete meaning of a sentence.

### Corpus Dependency

Predictions depend strongly on the vocabulary and word frequencies contained in the training corpus.

### No Personalization

The system does not learn individual user preferences, frequently used words, names, or writing style.

### Limited Error Understanding

Edit-distance-based correction focuses primarily on spelling similarity and may not understand the intended meaning.

For example:

```text
I went too the market.
```

The word `too` is correctly spelled but may need to be `to`.

An edit-distance algorithm cannot reliably solve this contextual problem.

### No Neural Language Model

Modern production keyboards use much more sophisticated machine-learning and neural language models capable of understanding context.

### Limited Vocabulary

Slang, abbreviations, technical terms, names, emojis, and multilingual text may not be handled effectively.

---

# 🚀 Production System Comparison

| Feature                  | This Project | Production Keyboard            |
| ------------------------ | ------------ | ------------------------------ |
| N-gram prediction        | ✅            | More advanced models           |
| Edit-distance correction | ✅            | Advanced contextual correction |
| Personalization          | ❌            | ✅                              |
| Context awareness        | Limited      | High                           |
| Large-scale vocabulary   | Limited      | Extensive                      |
| User-specific learning   | ❌            | ✅                              |
| Real-time adaptation     | Limited      | ✅                              |
| Neural models            | ❌            | ✅                              |
| Multilingual support     | Limited      | Extensive                      |

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
nltk
pyspellchecker
matplotlib
seaborn
jupyter
```

After installing NLTK, required resources can be downloaded using:

```python
import nltk

nltk.download("punkt")
nltk.download("stopwords")
```

---

# ▶️ How to Run

### 1. Clone the repository

```bash
git clone <your-github-repository-url>
```

### 2. Navigate to the project

```bash
cd OIBSIP/DataAnalytics-L2-AutocompleteAutocorrect
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Open Jupyter Notebook

```bash
jupyter notebook
```

### 5. Open

```text
NLP_Autocomplete_Autocorrect.ipynb
```

### 6. Run all cells

Execute the notebook from beginning to end to reproduce the preprocessing, model training, predictions, evaluation, and visualizations.

---

# 📸 Project Screenshots

The `screenshots/` folder contains visual outputs generated during the analysis:

* Top 20 word frequency chart
* Autocomplete predictions
* Autocorrect results
* Confusion matrix
* Algorithm comparison
* Performance metrics

---

# 🎓 Learning Outcomes

Through this project, the following concepts are demonstrated:

* Natural Language Processing
* Text preprocessing
* Tokenization
* Stopword removal
* Word frequency analysis
* N-gram language modeling
* Bigram and trigram models
* Autocomplete systems
* Edit distance
* Spelling correction
* Precision and recall
* Confusion matrix
* Algorithm comparison
* Data visualization
* NLP model evaluation

---

# 👨‍💻 Author

**Ratnesh Chauhan**

**OIBSIP – Data Analytics Internship**

---

# 📝 Conclusion

This project demonstrates how fundamental NLP techniques can be used to develop basic **autocomplete and autocorrect systems**.

The frequency-based bigram and trigram models provide a simple approach for next-word prediction, while edit-distance-based spelling correction helps identify and correct common typing mistakes.

The comparison highlights the trade-off between **simplicity, computational requirements, context awareness, and prediction accuracy**.

Although the implementation is simpler than production systems such as Google Keyboard, it provides a strong foundation for understanding how text prediction and spelling correction systems work and how their performance can be evaluated using quantitative metrics.
