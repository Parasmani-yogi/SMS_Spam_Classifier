# SMS_Spam_Classifier

A machine learning project to classify SMS messages as **spam** or **ham (non-spam)** using text preprocessing, vectorization, and machine learning models. The project also includes a **web interface using Streamlit** for interactive predictions.

---

## Table of Contents

- [Overview](#overview)  
- [Dataset](#dataset)  
- [Steps Involved](#steps-involved)  
- [Modeling & Evaluation](#modeling--evaluation)  
- [Final Model](#final-model)  
- [To Run](#to-run)  
- [Approach](#approach)  
- [Tools & Libraries](#tools--libraries)  

---

## Overview

This project classifies messages as **spam** or **ham**. It includes:

- Cleaning and preprocessing text data  
- Exploratory Data Analysis (EDA) to identify patterns  
- Feature extraction using **TF-IDF Vectorizer**  
- Training multiple classifiers and evaluating their performance  
- Selecting the best model based on **precision** and **accuracy**
  
---

## Dataset

The dataset used is `spam.csv` containing 5169 messages after cleaning:

| Column | Description |
|--------|-------------|
| `target` | Label: 0 → ham, 1 → spam |
| `text` | SMS message text |

> The dataset initially had 5572 entries and some unnecessary columns which were removed.

---

## Steps Involved

### 1. Data Cleaning
- Dropped unnecessary columns  
- Renamed columns for clarity  
- Removed duplicate entries  

### 2. Exploratory Data Analysis (EDA)
- Checked class balance: `ham` > `spam`  
- Visualized message lengths, words, and sentence counts  
- Histograms and pairplots for numeric features  

### 3. Text Preprocessing
- Convert to lowercase  
- Tokenization  
- Remove special characters and stopwords  
- Stemming using **PorterStemmer**  
- Created `transformed_text` column  

### 4. Feature Extraction
- Vectorized text using **TF-IDF Vectorizer** (max_features = 3000)  

### 5. Model Building
- Trained multiple classifiers: Logistic Regression, SVM, Naive Bayes, Decision Tree, Random Forest, AdaBoost, Bagging, Extra Trees, Gradient Boosting, XGBoost  
- Evaluated using **Accuracy** and **Precision**  

### 6. Model Improvement
- Used **Voting Classifier** (SVC + MultinomialNB + ExtraTrees)  
- Applied **Stacking Classifier** with Random Forest as final estimator  

---

## Modeling & Evaluation

| Model      | Accuracy | Precision |
|-----------|---------|-----------|
| MNB       | 0.971   | 1.0       |
| SVC       | 0.976   | 0.975     |
| BNB       | 0.984   | 0.992     |
| RFC       | 0.974   | 0.983     |
| Voting    | 0.980   | 0.983     |
| Stacking  | 0.979   | 0.939     |

**Observation:**  
- Spam messages tend to have longer texts and more words than ham messages.  
- TF-IDF features combined with **MultinomialNB** provided the best precision.  

---

## Final Model

- **Algorithm:** Multinomial Naive Bayes  
- **Vectorizer:** TF-IDF (max_features=3000)  
- **Saved files:**  
  - `vectorizer.pkl` → TF-IDF vectorizer  
  - `model.pkl` → Trained MultinomialNB model  

---

# To Run
Download the repository, then open the terminal and run:
```bash
streamlit run app.py
```
This will open the web page where you can input messages to check if they are spam or not.

---
# Approach
- Preprocessing: Convert all messages to lowercase, remove stopwords and punctuation, and apply stemming.
- Vectorization: Use TF-IDF to transform the cleaned text into numerical feature vectors.
- Model Training: Train multiple classifiers and evaluate based on accuracy and precision.
- Model Selection: Choose the model with the highest precision to reduce false positives for spam.

---
# Tools & Libraries
- Python 
- Pandas, NumPy
- Matplotlib, Seaborn
- NLTK (text preprocessing)
- Scikit-learn (models and vectorization)
- XGBoost
- Streamlit
- Pickle (saving models)





