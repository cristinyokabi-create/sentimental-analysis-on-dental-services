# sentimental-analysis-on-dental-services
This project applies Natural Language Processing (NLP) and machine learning techniques to analyze patient reviews of dental services. The goal is to classify sentiments (positive, neutral, negative) and extract recurring themes such as pain management, communication, empathy, and professionalism.
Sentiment Analysis of Patient Reviews on Dental Services
📘 Project Overview
This project applies Natural Language Processing (NLP) and machine learning to analyze patient reviews of dental services. The goal is to classify sentiments (positive, neutral, negative) and extract recurring themes such as pain management, communication, empathy, and professionalism.

By analyzing textual feedback, the project provides a more holistic understanding of patient satisfaction and service quality, beyond traditional star ratings.

🔍 Motivation
Dental visits often evoke strong emotions — fear, anxiety, satisfaction, or trust. Traditional evaluation methods (surveys, ratings) overlook these emotional dimensions. Sentiment analysis helps uncover hidden insights in patient reviews, supporting patient‑centered care and guiding improvements in dental services.

📂 Dataset
Source: Kaggle

Content: Dentist details, ratings, and patient review snippets.

Cleaning: Missing values removed, text standardized (lowercased, punctuation stripped, spaces normalized).

Format: CSV file with structured attributes and unstructured text.

🛠️ Tools & Technologies
Python (pandas, NumPy, scikit‑learn, NLTK, spaCy, TensorFlow/PyTorch)

Jupyter Notebook for cleaning, preprocessing, and experimentation

Excel for initial inspection and manual cleaning

Streamlit for building the interactive dashboard

⚙️ Methodology
Data Cleaning

Removed missing reviews, duplicates, standardized text.

Preprocessing

Tokenization, stopword removal, lemmatization, vectorization.

Modeling

Baseline models: Logistic Regression, Naïve Bayes, SVM.

Advanced models: LSTM, BERT.

Hybrid approaches combining lexicon‑based and machine learning methods.

Evaluation

Metrics: Accuracy, Precision, Recall, F1‑score, Sentiment Alignment, Theme Detection Accuracy.

Visualization

Sentiment distribution bar charts.

Word clouds for positive and negative reviews.

Theme frequency plots.

Dashboard for interactive exploration.

📊 Results & Insights
Majority of reviews are positive, reflecting high patient satisfaction.

Negative reviews highlight issues such as waiting times and pain management.

Common positive keywords: friendly, professional, recommend, comfortable.

Common negative keywords: wait, pain, anxious, problem.
