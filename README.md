```markdown
# Plotify 🎬

**Plotify** is a movie genre classification and content-based recommendation application built on top of the Wikipedia Movie Plots dataset. It processes, cleans, and lemmatizes raw movie synopses to enable multi-label genre classification and plot-based movie discovery.

```

---

## 📁 Project Structure

```text
Plotify/
├── data/
│   ├── raw/                  # Place the raw CSV dataset here (git-ignored)
│   └── processed/            # Processed Parquet dataset for ML & UI
├── notebooks/
│   └── CleaningData.ipynb    # Data cleaning & preprocessing notebook
├── requirements.txt          # Python dependencies
└── README.md                 # Project documentation

```

---

## 📊 Dataset Information

### 1. Raw Dataset

* **Source:** [Wikipedia Movie Plots (Kaggle)](https://www.kaggle.com/datasets/jrobischon/wikipedia-movie-plots?select=wiki_movie_plots_deduped.csv)
* **File:** `wiki_movie_plots_deduped.csv`
* **Instructions:** Download `wiki_movie_plots_deduped.csv` from the Kaggle link above and place it in the `data/raw/` directory before running the data cleaning notebook.

### 2. Processed Dataset

* **File:** `plotify_cleaned_movies.parquet`
* **Details:** Due to GitHub's file size limits for browser uploads, the preprocessed Parquet dataset can be downloaded directly from the **Releases** tab of this repository.
* **Schema:**
* `Title`: Movie title
* `Release Year`: Release year
* `Director`: Director metadata
* `GenreList`: Cleaned, multi-label list of top genres (preserved as native lists)
* `Plot`: Original full synopsis (for user display)
* `CleanPlot`: Lemmatized, lowercased, and tokenized text (for TF-IDF / feature extraction)



---

## 🚀 Getting Started

### Prerequisites

Ensure you have Python 3.9+ installed on your system.

### Installation

1. Clone the repository:
```bash
git clone [https://github.com/YOUR_USERNAME/Plotify.git](https://github.com/YOUR_USERNAME/Plotify.git)
cd Plotify

```


2. Install the required dependencies:
```bash
pip install -r requirements.txt

```


3. Download the NLTK stopwords and WordNet data (if running scripts manually):
```python
import nltk
nltk.download('stopwords')
nltk.download('wordnet')

```



---

## 🛠️ Data Processing Pipeline

The `notebooks/CleaningData.ipynb` notebook handles the data preparation pipeline:

1. **Filtering & Deduplication:** Removes records with missing plots, missing genres, or `'unknown'` values, and filters target origins/ethnicities.
2. **Genre Normalization:** Maps compound genre tags cleanly (preserving hyphenated tags like `sci-fi` and `rom-com`) and keeps top genre categories.
3. **Text Preprocessing:** Removes punctuation, lowercases synopses, strips stopwords, and applies two-pass lemmatization for optimal feature extraction.
4. **Optimized Export:** Saves the final dataset as a high-performance Apache Parquet file (`plotify_cleaned_movies.parquet`).

---

## 💻 Tech Stack

* **Language:** Python
* **Data Processing:** Pandas, NumPy, PyArrow
* **NLP & Text Mining:** NLTK (WordNet Lemmatizer, Stopwords), Regex

```

```
