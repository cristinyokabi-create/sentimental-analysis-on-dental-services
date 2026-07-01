# sentimental-analysis-on-dental-services
## Project Overview
This project applies Natural Language Processing (NLP) and machine learning to analyze patient reviews of dental services. The goal is to classify sentiments (positive, neutral, negative) and extract recurring themes such as pain management, communication, empathy, and professionalism.
By analyzing textual feedback, the project provides a more holistic understanding of patient satisfaction and service quality, beyond traditional star ratings.

## Motivation
Dental visits often evoke strong emotions — fear, anxiety, satisfaction, or trust. Traditional evaluation methods (surveys, ratings) overlook these emotional dimensions. Sentiment analysis helps uncover hidden insights in patient reviews, supporting patient‑centered care and guiding improvements in dental services.

## Dataset
Source: Kaggle
Content: Dentist details, ratings, and patient review snippets.
Cleaning: Missing values removed, text standardized (lowercased, punctuation stripped, spaces normalized).
Format: CSV file with structured attributes and unstructured text.

## Tools & Technologies
Python (pandas, NumPy, scikit‑learn, NLTK, spaCy, TensorFlow/PyTorch)
Jupyter Notebook for cleaning, preprocessing, and experimentation
Excel for initial inspection and manual cleaning
Streamlit for building the interactive dashboard

## Methodology
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

## Results & Insights
Majority of reviews are positive, reflecting high patient satisfaction.
Negative reviews highlight issues such as waiting times and pain management.
Common positive keywords: friendly, professional, recommend, comfortable.
Common negative keywords: wait, pain, anxious, problem.


# Dental Sentiment Dashboard

An interactive, browser-based dashboard for visualising sentiment analysis results from NYC dental clinic Google reviews. Built as a final project using Python (VADER NLP) and exported as a standalone HTML file.

---
## Project Overview

This project applies Natural Language Processing (NLP) to a dataset of 1,000 NYC dental clinic listings scraped from Google. Because most listings did not include a review snippet, the usable dataset after cleaning was **223 reviews**. Each review was processed through a full NLP pipeline and classified as positive, neutral, or negative using the VADER sentiment analyser.

---

## Files

| File | Description |
|------|-------------|
| `dental_sentiment_dashboard.html` | The interactive dashboard — open in any browser |
| `learnData.csv` | Raw dataset (1,000 clinic records) |
| `cleaned_learnData.xls` | Cleaned dataset (223 records with NLP outputs) |
| `finalProject.ipynb` | Python notebook with the full analysis pipeline |
| `README.md` | This file |

---

## Dataset

**Raw data (`learnData.csv`)** — 1,000 records, 6 columns:

- `name` — clinic name
- `address` — street address (New York City)
- `phone` — contact number
- `website` — clinic website (320 missing)
- `rating` — Google star rating (777 missing)
- `reviewSnippet` — short review text (777 missing)

**Cleaned data (`cleaned_learnData.xls`)** — 223 records, 12 columns, adds:

- `clean_text` — lowercased, punctuation-removed text
- `tokens` — word tokens
- `tokens_no_stop` — tokens with stopwords removed
- `lemmatized_tokens` — tokens reduced to root form
- `sentiment_score` — VADER compound score (range: −1 to +1)
- `sentiment_label` — classified as `positive`, `neutral`, or `negative`

---

## NLP Pipeline

```
Raw text
  → Lowercase & clean punctuation
  → Tokenise
  → Remove stopwords
  → Lemmatise (WordNetLemmatizer)
  → TF-IDF vectorisation
  → VADER sentiment scoring
  → Label assignment
```

**VADER labelling thresholds:**

| Score range | Label |
|-------------|-------|
| ≥ 0.05 | Positive |
| −0.05 to 0.05 | Neutral |
| ≤ −0.05 | Negative |

---

## Key Results

| Metric | Value |
|--------|-------|
| Total clinics in raw data | 1,000 |
| Reviews with text (after cleaning) | 223 |
| Positive sentiment | 207 (92.8%) |
| Neutral sentiment | 5 (2.2%) |
| Negative sentiment | 11 (4.9%) |
| Average star rating | 4.98 / 5.0 |
| Sentiment score range | −0.69 to +0.97 |

**Top keywords in positive reviews:** dentist, great, always, staff, care, patient

---

## Model Comparison

Four classifiers were trained on the labelled data using TF-IDF features:

| Model | Accuracy |
|-------|----------|
| LinearSVC *(best)* | 85% |
| Logistic Regression | 82% |
| Random Forest | 78% |
| Naive Bayes | 75% |

LinearSVC performed best, which is typical for sparse, high-dimensional text data.

---

## Dashboard Features

The dashboard (`dental_sentiment_dashboard.html`) is fully self-contained — all data is embedded in the file. No server or internet connection is needed after the initial Chart.js library load.

**Summary metrics** — total clinics, reviews analysed, positive sentiment %, and average rating.

**Charts:**
- Doughnut chart of sentiment split (positive / neutral / negative)
- Bar chart of star rating distribution
- Histogram of VADER compound scores across all 223 reviews (red = negative range, green = positive range)

**Model comparison panel** — horizontal bar chart comparing accuracy of all four classifiers.

**Top keywords** — most frequent lemmatised terms in positive reviews.

**Review Explorer** — interactive table with:
- Live search by clinic name or review text
- Filter by sentiment label (positive / neutral / negative)
- Filter by star rating
- Paginated results (10 per page)
- Colour-coded sentiment badges and score bars per row

---

## How to Open the Dashboard

1. Download `dental_sentiment_dashboard.html`
2. Double-click the file — it opens in your default browser
3. No installation, no Python, no server required

> The dashboard loads Chart.js from a CDN (`cdn.jsdelivr.net`). An internet connection is needed on first load for the charts to render. The review data itself is fully embedded and works offline.

---

## Dependencies (Python Notebook)

```
pandas
nltk
scikit-learn
vaderSentiment
openpyxl / xlrd
```

Install with:

```bash
pip install pandas nltk scikit-learn vaderSentiment openpyxl
```

Also download NLTK data inside the notebook:

```python
import nltk
nltk.download('stopwords')
nltk.download('wordnet')
nltk.download('punkt')
