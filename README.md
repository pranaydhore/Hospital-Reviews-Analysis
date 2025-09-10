<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Hospital Reviews Analysis — Project README</title>
  <style>
    :root{--bg:#0f1724;--card:#0b1220;--accent:#ef4444;--muted:#94a3b8;--glass:rgba(255,255,255,0.04)}
    html,body{height:100%;margin:0;font-family:Inter,ui-sans-serif,system-ui,Arial;background:linear-gradient(180deg,#071029 0%, #071a2f 60%);color:#e6eef8}
    header{padding:36px 6%;display:flex;align-items:center;gap:20px}
    .logo{width:72px;height:72px;display:grid;place-items:center;border-radius:14px;background:linear-gradient(135deg,var(--accent),#ff7b7b);box-shadow:0 10px 30px rgba(239,68,68,0.18);transform:rotate(-12deg)}
    h1{font-size:28px;margin:0}
    p.lead{color:var(--muted);margin:6px 0 0}
    main{padding:24px 6%;display:grid;grid-template-columns:1fr 420px;gap:24px}
    .card{background:var(--card);border-radius:14px;padding:18px;box-shadow:0 6px 30px rgba(2,6,23,0.6);backdrop-filter:blur(6px);border:1px solid rgba(255,255,255,0.03)}
    .section-title{display:flex;align-items:center;gap:10px}
    .pill{padding:6px 10px;background:var(--glass);border-radius:999px;color:var(--muted);font-size:13px}
    pre{background:#051226;padding:12px;border-radius:10px;overflow:auto;color:#d6f3ff}
    code{font-family:monospace;font-size:13px}
    .grid{display:grid;gap:12px}
    .meta{display:flex;flex-direction:column;gap:6px}
    .animated-blob{position:relative;width:100%;height:140px;border-radius:12px;background:linear-gradient(90deg, rgba(239,68,68,0.18), rgba(59,130,246,0.12));overflow:hidden}
    .blob{position:absolute;filter:blur(36px);opacity:0.9;animation:float 6s ease-in-out infinite}
    .blob.b1{width:240px;height:240px;background:radial-gradient(circle at 30% 30%, rgba(239,68,68,0.6), rgba(239,68,68,0.05));left:-40px;top:-60px}
    .blob.b2{width:300px;height:300px;background:radial-gradient(circle at 70% 70%, rgba(59,130,246,0.5), rgba(59,130,246,0.02));right:-60px;bottom:-80px;animation-duration:8s}
    @keyframes float{0%{transform:translateY(0) rotate(0)}50%{transform:translateY(-18px) rotate(8deg)}100%{transform:translateY(0) rotate(0)}}
    .cta{display:inline-block;padding:10px 14px;border-radius:10px;background:linear-gradient(90deg,var(--accent),#ff7b7b);color:white;text-decoration:none;font-weight:600}
    footer{padding:18px 6%;color:var(--muted);font-size:13px}
    .code-title{display:flex;justify-content:space-between;align-items:center}
    .small{font-size:13px;color:var(--muted)}
    /* responsive */
    @media(max-width:980px){main{grid-template-columns:1fr;padding:18px}header{flex-direction:column;align-items:flex-start}} 
  </style>
</head>
<body>
  <header>
    <div class="logo">HR</div>
    <div>
      <h1>Hospital Reviews Analysis</h1>
      <p class="lead">Complete project README — Python (Jupyter) preprocessing, NLP & sentiment; Power BI dashboards with DAX. Animated, copy-ready HTML.</p>
    </div>
  </header>

  <main>
    <section class="card">
      <div class="section-title">
        <div class="pill">Overview</div>
        <div style="margin-left:auto" class="small">Updated: Sep 10, 2025</div>
      </div>
      <div style="height:14px"></div>
      <div class="grid">
        <div class="animated-blob">
          <div class="blob b1"></div>
          <div class="blob b2"></div>
        </div>

   <div class="meta">
          <p style="margin:0">This project ingests hospital review data (CSV), performs cleaning, exploratory analysis, and NLP-based sentiment classification in a Jupyter Notebook (Python). Final visualizations and interactive storytelling are implemented in Power BI (.pbix). Use the notebook for reproducible data work and Power BI for stakeholder-facing dashboards.</p>

  <ul class="small">
            <li><strong>Files included:</strong> /mnt/data/Hospital ER_Data.csv, /mnt/data/Hospital Reviews Analysis.ipynb, /mnt/data/hospital.pbix</li>
            <li><strong>Languages / Tools:</strong> Python (pandas, nltk/spacy, sklearn, transformers optional), Jupyter Notebook, Power BI (DAX)</li>
          </ul>
        </div>

   <div>
          <div class="code-title"><strong>How to run (quick)</strong><span class="small">Local / Colab</span></div>
          <ol class="small">
            <li>Open the Jupyter Notebook: <code>/mnt/data/Hospital Reviews Analysis.ipynb</code>.</li>
            <li>Install requirements: <code>pip install pandas nltk scikit-learn textblob spacy</code></li>
            <li>Load CSV: <code>pd.read_csv('/mnt/data/Hospital ER_Data.csv')</code></li>
            <li>Open Power BI file: <code>/mnt/data/hospital.pbix</code> (Power BI Desktop).</li>
          </ol>
        </div>
      </div>
    </section>

  <aside class="card">
      <h3 style="margin-top:0">At a glance</h3>
      <div class="small">Project components</div>
      <ul class="small">
        <li><strong>Data ingestion:</strong> read CSV, validate schema, cast datatypes</li>
        <li><strong>Preprocessing:</strong> text cleaning, stopwords, lemmatization, metadata extraction (date, department)</li>
        <li><strong>Feature engineering:</strong> length, sentiment scores, topic keywords, TF-IDF</li>
        <li><strong>Modeling:</strong> rule-based sentiment or ML classifier (Logistic/Naive Bayes); transformer optional</li>
        <li><strong>Power BI:</strong> interactive dashboards, slicers, KPI cards, custom visuals</li>
      </ul>

      <div style="height:10px"></div>
      <div class="small"><strong>Useful paths</strong>
        <pre><code>/mnt/data/Hospital ER_Data.csv
/mnt/data/Hospital Reviews Analysis.ipynb
/mnt/data/hospital.pbix</code></pre>
      </div>

   <a class="cta" href="#dax">Jump to DAX</a>
    </aside>

   <section class="card" style="grid-column:1/-1;margin-top:12px">
      <div class="section-title"><div class="pill">Detailed Walkthrough</div></div>
      <div style="height:8px"></div>

   <h4>1. Data Loading & Validation (Python)</h4>
      <pre><code># sample
import pandas as pd
df = pd.read_csv('/mnt/data/Hospital ER_Data.csv')
# quick checks
print(df.info())
print(df.isnull().sum())
</code></pre>

  <h4>2. Text Preprocessing</h4>
      <pre><code># cleaning pipeline (example)
import re
from nltk.corpus import stopwords
from nltk.stem import WordNetLemmatizer

def clean_text(t):
    t = str(t).lower()
    t = re.sub(r"http\S+|www\S+","", t)
    t = re.sub(r"[^a-z0-9\s]","", t)
    words = [w for w in t.split() if w not in stopwords.words('english')]
    return ' '.join(words)

# apply
# df['clean'] = df['review_text'].apply(clean_text)
</code></pre>

   <h4>3. Sentiment Analysis</h4>
      <pre><code># simple approach with TextBlob
from textblob import TextBlob

def sentiment_label(text):
    s = TextBlob(text).sentiment.polarity
    if s > 0.1: return 'Positive'
    if s < -0.1: return 'Negative'
    return 'Neutral'

# df['sentiment'] = df['clean'].apply(sentiment_label)
</code></pre>

  <h4>4. Topic extraction & keywords</h4>
      <pre><code># TF-IDF + top-n terms per cluster / topic
from sklearn.feature_extraction.text import TfidfVectorizer
vect = TfidfVectorizer(max_df=0.8, min_df=5, ngram_range=(1,2))
X = vect.fit_transform(df['clean'].fillna(''))
# then use clustering or LDA
</code></pre>

   <h4 id="dax">5. Power BI & DAX — sample queries</h4>
      <p class="small">Below are practical DAX snippets you can paste into measures in Power BI Desktop to calculate KPIs.</p>

   <pre><code># Average Rating (measure)
Average Rating = AVERAGE('Reviews'[Rating])

# Sentiment distribution (counts)
Positive Reviews = CALCULATE(COUNTROWS('Reviews'), 'Reviews'[Sentiment] = "Positive")

# 30-day rolling average of rating
Rolling Rating 30d =
VAR Latest = MAX('Reviews'[ReviewDate])
RETURN
CALCULATE(
    AVERAGE('Reviews'[Rating]),
    DATESINPERIOD('Reviews'[ReviewDate], Latest, -30, DAY)
)

# Top complaints (by keyword tag)
Top Complaints =
TOPN(10, SUMMARIZE('Reviews', 'Reviews'[Keyword], "Cnt", COUNTROWS('Reviews')), [Cnt], DESC)
</code></pre>

   <h4>6. Recommended Power BI visuals & UX</h4>
      <ul class="small">
        <li>KPI cards: Overall rating, %Positive, %Negative, Avg response time</li>
        <li>Sentiment trend: line chart with 7/30 day rolling averages</li>
        <li>Department heatmap: average rating by department & location</li>
        <li>Word cloud / top keywords with slicers (time, dept)</li>
        <li>Table of flagged reviews for manual auditing (search & export)</li>
      </ul>

   <h4>7. Tips for production & scaling</h4>
      <ol class="small">
        <li>Store cleaned dataset in a central store (Azure Blob / SQL) and refresh Power BI dataset.</li>
        <li>Use incremental refresh for large review volumes.</li>
        <li>Consider an ML model (transformers) for higher-accuracy sentiment and aspect-based sentiment analysis.</li>
        <li>Expose an export of flagged negative reviews for case management.</li>
      </ol>

   </section>

  </main>

  <footer>
    <div class="card" style="display:flex;justify-content:space-between;align-items:center">
      <div>
        <div style="font-weight:700">Get started</div>
        <div class="small">Open the notebook and run cells, then open the PBIX in Power BI Desktop. For help integrating with a database, see the notebook instructions.</div>
      </div>
      <div style="text-align:right">
        <div class="small">Paths</div>
        <div style="font-family:monospace">/mnt/data/Hospital ER_Data.csv</div>
      </div>
    </div>
    <div style="height:8px"></div>
    <div class="small">Generated README • If you want I can also export a printable PDF or a condensed one-page version.</div>
  </footer>

  <script>
    // small interactive behaviour: smooth anchor scrolling
    document.querySelectorAll('a[href^="#"]').forEach(a=>{
      a.addEventListener('click', e=>{e.preventDefault();document.querySelector(a.getAttribute('href')).scrollIntoView({behavior:'smooth'});});
    });
  </script>
</body>
</html>
