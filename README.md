# Phishing URL Detection Project

A comparison of two machine learning approaches for phishing URL detection using the Malicious URLs dataset: a structured feature Random Forest classifier and a TF‑IDF vectorization Logistic Regression classifier.

---

## Requirements

**Python version**  
- Python 3.8 or later

**Python packages**  
Install required packages with pip:

```bash
pip install pandas numpy scikit-learn matplotlib jupyter
```

---

## Project Files

| File | Description |
|---|---|
| `malicious_phish.csv` | Raw dataset of labeled URLs |
| `Structured Feature-Based Random Forest.ipynb` | Notebook implementing lexical feature extraction and Random Forest |
| `TF-IDF Vectorization.ipynb` | Notebook implementing character n-gram TF‑IDF and Logistic Regression |

---

## How to Run

### 1 Start Jupyter Notebook

```bash
jupyter notebook
```

Open the notebook you want to run from the Jupyter interface.

### 2 Structured Feature Random Forest Notebook

1. Open `Structured Feature-Based Random Forest.ipynb`.  
2. Ensure `malicious_phish.csv` is in the same working directory.  
3. Run cells in order to:
   - Load and clean the dataset
   - Extract lexical features (URL length, digit count, special characters, IP presence)
   - Split data (70% train, 15% validation, 15% test)
   - Train Random Forest (`n_estimators=100`, `random_state=42`)
   - Evaluate metrics and display feature importances and confusion matrix

### 3 TF‑IDF Vectorization Logistic Regression Notebook

1. Open `TF-IDF Vectorization.ipynb`.  
2. Ensure `malicious_phish.csv` is in the same working directory.  
3. Run cells in order to:
   - Load and clean the dataset
   - Map labels to binary (phishing = 1, others = 0)
   - Vectorize URLs using `TfidfVectorizer(analyzer='char_wb', ngram_range=(3,5))`
   - Split data (70% train, 15% validation, 15% test)
   - Train Logistic Regression (`max_iter=1000`, `random_state=42`)
   - Evaluate metrics and display classification report and confusion matrix

---

## Reproducing Results and Expected Outputs

**Dataset split**  
- 70% training, 15% validation, 15% test (use `stratify=y` for reproducibility)

**Key metrics to expect**  
- Accuracy, Precision, Recall, F1 score for each model  
- Confusion matrices and feature importance for Random Forest

**Random seeds**  
- Use `random_state=42` for model training and `train_test_split` to reproduce reported results.

---

## Notes and Best Practices

- **Data location**: place `malicious_phish.csv` in the same folder as the notebooks.  
- **Label mapping**: ensure phishing labels are mapped to `1` and all other categories to `0`.  
- **Sanitisation**: remove duplicates and rows with missing `url` or `type` before feature extraction.  
- **Performance**: TF‑IDF with character n‑grams typically captures obfuscation patterns better than simple lexical features; consider more advanced models for concept drift mitigation.  
- **AI assistance**: portions of code may have been generated with AI tools; review and test all code before deployment.
