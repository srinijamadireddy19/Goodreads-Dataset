---

# Goodreads Emotional Intelligence Engine

### Transformer-Based Emotion Analysis of Large-Scale Book Reviews

---

## Project Summary

Numeric star ratings oversimplify reader experience.
This project builds an **Emotion Intelligence Engine** for Goodreads reviews using **emotion-aware transformer models**, uncovering nuanced emotional patterns that ratings alone fail to capture.

By analyzing **millions of reviews**, the system generates **book-level emotional fingerprints**, tracks **emotion trends over time**, and identifies **rating–emotion mismatches** (e.g., highly rated books with emotionally conflicted readers).

---

## Key Contributions

* **Emotion-aware NLP pipeline** using transformer models trained on labeled emotion data
* **Book-level emotional profiling** beyond binary sentiment
* **Emotion vs Rating mismatch analysis** (behavioral insight, not surface metrics)
* **Temporal emotion trend analysis** for popular books
* Clear justification of **why unsupervised embedding clustering was insufficient**

This is an **analysis-driven NLP project**, not a sentiment demo.

---

## Technical Approach

### 1. Data

* Goodreads **Book Metadata** (title, author, genres, average rating)
* Goodreads **User Reviews** (text, rating, timestamp)

### 2. Preprocessing

* HTML & noise removal
* Text normalization and truncation (512 tokens)
* Rating normalization
* Review–book merge via `book_id`

---

### 3. Emotion Detection (Core NLP Component)

Instead of unsupervised clustering, the project uses a **GoEmotions-based DistilRoBERTa transformer**, trained explicitly for emotion recognition.

**Predicted emotions:**

* `joy`
* `sadness`
* `anger`
* `fear`
* `surprise`
* `disgust`
* `neutral`

Each review produces:

* **Emotion label**
* **Emotion confidence score**

This ensures **interpretability and methodological correctness**.

---

### 4. Book-Level Emotional Fingerprints

For each book:

* Aggregate emotion distribution (% of reviews per emotion)
* Identify dominant and minority emotional tones
* Compare with `average_rating`

This enables detection of:

*  *Highly rated but emotionally conflicted books*
*  *Moderately rated but emotionally positive books*

---

### 5. Temporal Emotion Analysis

* Monthly aggregation of emotions for popular books
* Visualization of emotional drift over time
* Detection of reread effects, hype cycles, and perception shifts

---

##  Example Insights

* 5⭐ ratings frequently coexist with **sadness or frustration**
* 3⭐ reviews often show **strong emotional polarity**
* Emotion trends change over years, even when ratings remain stable
* Authors vary significantly in **emotional consistency**

---

##  Methodological Decision (Important)

Initial experiments using **BERT embeddings + KMeans clustering** revealed dominance of narrative and stylistic patterns rather than emotional separation.

 **Pivoted to emotion-aware transformers** to ensure:

* Valid emotional grounding
* Reproducibility
* Defensible interpretation

This design choice reflects **research-grade NLP practice**.

---

##  Tech Stack

* **Python**
* **Hugging Face Transformers**
* **DistilRoBERTa (Emotion Classification)**
* **Pandas, NumPy**
* **Scikit-learn**
* **Matplotlib, Seaborn**
* **Kaggle**

---

##  Notebook Execution Order

This project is organized as a **sequential notebook pipeline**.
To reproduce results correctly, notebooks **must be run in the following order**:

1. **`goodreads-dataset-cleaning.ipynb`**

   * Loads raw Goodreads datasets
   * Cleans and normalizes review text
   * Merges reviews with book metadata
   * Outputs processed datasets for downstream analysis

2. **`goodreads-dataset-eda.ipynb`**

   * Performs exploratory data analysis on cleaned data
   * Examines rating distributions, review lengths, and metadata patterns
   * Validates data quality before modeling

3. **`goodreads-dataset-sentiment-insights.ipynb`**

   * Applies the **emotion-aware DistilRoBERTa transformer**
   * Predicts fine-grained emotions for each review
   * Generates per-book emotional distributions

4. **`goodreads-bert-embedding-sentiment.ipynb`**

   * Compares emotional fingerprints with average star ratings
   * Identifies emotion–rating mismatches
   * Analyzes temporal emotion trends

⚠️ **Note:**
Skipping or reordering notebooks may lead to missing files or inconsistent results, as each notebook depends on outputs from the previous stage.

---

##  Future Work

* Emotion-aware book recommendation system
* Genre-level emotional fingerprints
* Interactive dashboard (Streamlit / Power BI)
* Fine-tuning emotion models on Goodreads-specific data
* Cross-lingual emotion analysis

---

##  Key Takeaway

> **Ratings express judgment.
> Emotions reveal experience.**

Transformer-based emotion analysis provides a deeper, behavior-level understanding of reader perception than numeric ratings alone.

---

## 👤 Author

**Srinija Madireddy**
B.Tech — Data Science
NLP · Deep Learning · Applied Machine Learning

