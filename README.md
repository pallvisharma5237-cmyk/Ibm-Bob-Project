# 💊 Drug Recommendation & Analysis Platform

A full-stack ML web application built with **Python + Streamlit** that analyses 53,000+ patient drug reviews to provide:

- 🔬 **Condition Classification** — predict a patient's medical condition from their review
- ⭐ **Rating Prediction** — predict a drug's rating (1–10) from review text  
- 💬 **Sentiment Analysis** — positive / neutral / negative labelling + helpfulness drivers
- 📊 **Data Visualisations** — interactive EDA dashboard (drugs, conditions, trends)
- 💊 **Drug Recommender** — enter a condition, get the best drugs ranked by evidence

---

## 📁 Project Structure

```
drug_recommendation_app/
├── app.py                          # Main Streamlit entry point (landing page)
├── requirements.txt                # Python dependencies
├── data/
│   └── drugsComTest_raw.csv        # UCI Drug Review dataset
├── src/
│   ├── preprocessing.py            # Data loading, cleaning, feature engineering
│   ├── models.py                   # ML pipelines (classifier, regressor, sentiment)
│   ├── visualizations.py           # All Plotly chart functions
│   ├── recommender.py              # Drug recommendation engine
│   └── utils.py                    # Streamlit cache helpers + UI utilities
└── pages/
    ├── 1_Overview.py               # EDA dashboard
    ├── 2_Condition_Classifier.py   # TF-IDF + Logistic Regression
    ├── 3_Rating_Predictor.py       # TF-IDF + Ridge Regression
    ├── 4_Sentiment_Analysis.py     # TextBlob sentiment + helpfulness
    └── 5_Drug_Recommender.py       # Recommendation engine UI
```

---

## 🚀 Quick Start

### 1. Install dependencies

```bash
cd drug_recommendation_app
pip install -r requirements.txt
```

### 2. Download NLTK data (first run only)

```python
python -c "import nltk; nltk.download('punkt'); nltk.download('stopwords')"
```

### 3. Run the app

```bash
streamlit run app.py
```

The app opens at **http://localhost:8501** in your browser.

---

## 🧠 ML Models

| Module | Algorithm | Features | Target |
|--------|-----------|----------|--------|
| Condition Classifier | TF-IDF + Logistic Regression | Review text | Medical condition (top 30) |
| Rating Predictor | TF-IDF + Ridge Regression | Review text | Rating 1–10 |
| Sentiment Analyser | TextBlob (rule-based) | Review text | Positive / Neutral / Negative |

All models are trained on-the-fly at startup and **cached** with `@st.cache_resource` so they only train once per session.

---

## 📊 Dataset

**UCI Drug Reviews Dataset** — `drugsComTest_raw.csv`https://www.kaggle.com/datasets/jessicali9530/kuc-hackathon-winter-2018

| Column | Description |
|--------|-------------|
| `uniqueID` | Row identifier |
| `drugName` | Name of the drug |
| `condition` | Patient's condition |
| `review` | Patient's free-text review |
| `rating` | Drug rating (1–10) |
| `date` | Review date |
| `usefulCount` | How many users found the review helpful |

---

## 📦 Key Libraries

| Library | Purpose |
|---------|---------|
| `streamlit` | Frontend web UI |
| `scikit-learn` | ML pipelines (TF-IDF, LR, Ridge) |
| `textblob` | Sentiment analysis |
| `plotly` | Interactive charts |
| `pandas / numpy` | Data processing |

---

## ⚠️ Disclaimer

This application is for **educational and research purposes only**.  
It is **not** a substitute for professional medical advice, diagnosis, or treatment.
