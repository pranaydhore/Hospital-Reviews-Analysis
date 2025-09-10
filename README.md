# 🏥 Hospital Reviews Analysis — Detailed Project Documentation

This document provides an in-depth explanation of the **Hospital Reviews Analysis** project, which combines the power of **Python (Jupyter Notebook)** and **Power BI** to extract meaningful insights from hospital reviews. The project aims to help hospitals and healthcare providers understand patient experiences, satisfaction levels, and recurring issues through **data-driven analysis**.

---

## 📖 Introduction

In today’s healthcare system, patient feedback plays a vital role in evaluating the quality of medical services. Reviews often highlight not only positive experiences but also areas where hospitals can improve, such as waiting times, staff behavior, billing procedures, and cleanliness. However, reviews are typically unstructured text, making it difficult for organizations to analyze them at scale.

This project addresses this challenge by:
- Cleaning and preprocessing raw hospital review data.
- Applying **Natural Language Processing (NLP)** to classify sentiment and extract keywords.
- Using **statistical analysis** and machine learning to identify patterns.
- Building **Power BI dashboards** powered by **DAX measures** for interactive visualization.

The outcome provides hospital administrators with actionable insights into **patient satisfaction trends, problem areas, and overall service quality.**

---

## 🎯 Objectives
1. **Data Preprocessing**: Handle missing values, remove noise, normalize text.
2. **Sentiment Analysis**: Classify reviews as positive, negative, or neutral.
3. **Keyword & Topic Extraction**: Identify frequent terms that highlight complaints or praises.
4. **Statistical Summaries**: Measure distributions of ratings and sentiments.
5. **Dashboard Building**: Visualize insights in an interactive, easy-to-use interface.
6. **Actionable Insights**: Provide recommendations to improve hospital services.

---

## 📂 Dataset

### Files Included:
- **`Hospital ER_Data.csv`** → Contains patient reviews, ratings, dates, and department info.
- **`Hospital Reviews Analysis.ipynb`** → Jupyter Notebook with data preprocessing, sentiment analysis, and feature extraction.
- **`hospital.pbix`** → Power BI dashboard with DAX measures and visualizations.

### Data Attributes:
- **Review Text** → Written patient feedback.
- **Rating** → Numerical score (e.g., 1–5 stars).
- **Review Date** → Date of feedback.
- **Department/Service** → Hospital department related to the review.

---

## ⚙️ Methodology

### 🔹 Step 1: Data Preprocessing (Python)
Raw hospital reviews contain typos, slang, and irrelevant text. Preprocessing ensures data consistency and quality.

**Techniques Used:**
- Lowercasing all text.
- Removing punctuation, special symbols, and URLs.
- Stopword removal (e.g., "the", "is", "at").
- Lemmatization for word normalization (e.g., “caring” → “care”).
- Handling missing or duplicate entries.

```python
import pandas as pd
import re
from nltk.corpus import stopwords
from nltk.stem import WordNetLemmatizer

# Load data
df = pd.read_csv("Hospital ER_Data.csv")

# Clean text function
def clean_text(text):
    text = str(text).lower()
    text = re.sub(r"http\S+|www\S+", "", text)
    text = re.sub(r"[^a-z0-9\s]", "", text)
    words = [w for w in text.split() if w not in stopwords.words('english')]
    return " ".join(words)

# Apply preprocessing
df["Cleaned_Review"] = df["Review"].apply(clean_text)
```

---

### 🔹 Step 2: Sentiment Analysis

Using **TextBlob** for a simple yet effective polarity-based classification:
- **Positive** → Polarity > 0.1
- **Negative** → Polarity < -0.1
- **Neutral** → Otherwise

```python
from textblob import TextBlob

def sentiment_label(text):
    s = TextBlob(text).sentiment.polarity
    if s > 0.1:
        return "Positive"
    elif s < -0.1:
        return "Negative"
    else:
        return "Neutral"

# Apply sentiment analysis
df["Sentiment"] = df["Cleaned_Review"].apply(sentiment_label)
```

This produces a new column, `Sentiment`, that categorizes each review.

---

### 🔹 Step 3: Keyword & Topic Extraction

To identify **frequent complaints and praises**, we apply **TF-IDF (Term Frequency–Inverse Document Frequency)** and clustering.

```python
from sklearn.feature_extraction.text import TfidfVectorizer

vect = TfidfVectorizer(max_df=0.8, min_df=5, ngram_range=(1,2))
X = vect.fit_transform(df["Cleaned_Review"].fillna(""))
```

These features can be used for:
- Word clouds.
- Clustering similar reviews.
- Identifying **department-specific issues**.

---

### 🔹 Step 4: Statistical Analysis

With Python’s **pandas** and **matplotlib**, we calculate:
- Average rating.
- Distribution of sentiments.
- Review frequency trends.
- Correlation between ratings and review length.

```python
import matplotlib.pyplot as plt

sentiment_counts = df["Sentiment"].value_counts()
plt.bar(sentiment_counts.index, sentiment_counts.values)
plt.title("Sentiment Distribution")
plt.show()
```

---

### 🔹 Step 5: Visualization in Power BI

Once the processed dataset is saved as a CSV/Excel, it is imported into **Power BI Desktop** for advanced visualization. Here, **DAX (Data Analysis Expressions)** is used to create measures.

#### Example DAX Measures:
```DAX
-- Average Rating
Average Rating = AVERAGE('Reviews'[Rating])

-- Positive Review Count
Positive Reviews = 
CALCULATE(
    COUNTROWS('Reviews'),
    'Reviews'[Sentiment] = "Positive"
)

-- Rolling 30-day Average Rating
Rolling Rating 30d =
VAR Latest = MAX('Reviews'[ReviewDate])
RETURN
CALCULATE(
    AVERAGE('Reviews'[Rating]),
    DATESINPERIOD('Reviews'[ReviewDate], Latest, -30, DAY)
)

-- Top Complaints (by keyword)
Top Complaints =
TOPN(10, SUMMARIZE('Reviews', 'Reviews'[Keyword], "Cnt", COUNTROWS('Reviews')), [Cnt], DESC)
```

#### Recommended Visuals:
- **KPI Cards** → Overall rating, % Positive reviews, % Negative reviews.
- **Line Chart** → Sentiment trend over time.
- **Heatmap** → Department-wise average ratings.
- **Word Cloud** → Frequent complaint keywords.
- **Tables** → Negative reviews for manual follow-up.

---

## 📊 Insights & Findings

From initial analysis, key insights include:
- **Positive sentiment dominates**, but negative reviews highlight specific recurring issues.
- **Departments with long waiting times** tend to receive lower ratings.
- **Billing and administrative processes** often appear in negative feedback.
- **Staff friendliness** is the most common positive keyword.

---

## ⚡ Quick Start

### Python Setup
```bash
# Install required libraries
pip install pandas nltk scikit-learn textblob matplotlib

# Run the notebook
jupyter notebook "Hospital Reviews Analysis.ipynb"
```

### Power BI Setup
1. Open `hospital.pbix` in Power BI Desktop.
2. Connect to processed CSV data.
3. Explore dashboards and apply filters.

---

## 🛠 Tech Stack
- **Programming**: Python (pandas, nltk, scikit-learn, TextBlob)
- **Visualization**: Power BI (DAX, custom visuals)
- **Notebook Environment**: Jupyter Notebook

---

## ✅ Conclusion

The **Hospital Reviews Analysis Project** demonstrates how combining **data science techniques** with **business intelligence tools** can generate actionable insights. Hospitals can leverage this system to:
- Continuously monitor patient satisfaction.
- Detect common issues and complaints.
- Identify areas of strength and opportunities for improvement.
- Support evidence-based decision-making.

Ultimately, this leads to **better patient experiences and improved healthcare quality.**

---

## 📌 Future Enhancements
1. **Aspect-based Sentiment Analysis** → Detect sentiment toward specific services (e.g., doctors, staff, facilities).
2. **Real-time Dashboard Refresh** → Integrate live streaming of reviews.
3. **Advanced Machine Learning Models** → Apply transformers (e.g., BERT) for higher accuracy.
4. **Integration with Hospital Systems** → Automate complaint redirection and case management.

---

## 📝 Author
**Pranay Dhore** — Data Analyst | AI & BI Enthusiast  
📧 pranaydhore03@gmail.com
