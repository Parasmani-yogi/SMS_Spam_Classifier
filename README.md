# To Run
Download the repository, then open the terminal and run:
```bash
streamlit run app.py
```
This will open the web page where you can input messages to check if they are spam or not.

# Approach
This project classifies messages as spam or ham. The text is preprocessed by lowercasing, removing punctuation and stopwords, and stemming. Messages are converted into numeric vectors using TF-IDF. Multiple machine learning models were trained, and the Multinomial Naive Bayes (MNB) model was selected for its high precision (1.0) and strong accuracy (~97%). The model and vectorizer are saved using pickle, and Streamlit is used to build a simple web interface for predicting new messages.
