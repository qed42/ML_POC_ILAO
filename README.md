<h1 align="center">⚖️ ML_POC_ILAO</h1>

<p align="center">
  <em>A proof-of-concept comparing DistilBERT, Logistic Regression, and Random Forest for classifying legal aid queries — built for the Illinois Legal Aid Online (ILAO) use case.</em>
</p>

<p align="center">
  <img alt="status" src="https://img.shields.io/badge/status-proof--of--concept-orange">
  <img alt="language" src="https://img.shields.io/badge/notebooks-Jupyter-informational">
  <img alt="maintainer" src="https://img.shields.io/badge/maintained%20by-QED42-blue">
</p>

<p align="center">
  <a href="#-overview">Overview</a> •
  <a href="#-models-compared">Models</a> •
  <a href="#-repository-structure">Structure</a> •
  <a href="#%EF%B8%8F-setup">Setup</a> •
  <a href="#-usage">Usage</a> •
  <a href="#-datasets">Datasets</a>
</p>

---

## 📋 Overview

This repository explores how different machine learning techniques classify incoming legal aid queries. It's an exploratory POC — models are trained on small, mostly synthetic query datasets to compare trade-offs in accuracy, interpretability, and complexity before committing to one approach for a production pipeline.

The goal isn't to pick a single "winner." It's to map each model's strengths to the kind of query it handles best, so a future routing layer can apply the right model per query type instead of forcing every query through one approach.

## 🧠 Models Compared

| Model | Notebook | Strengths | Best suited for |
|---|---|---|---|
| 🤖 **DistilBERT** | `DistiledBert.ipynb` | Understands query semantics and context | Complex or conversational natural language queries |
| 📈 **Logistic Regression** | `Logistic_Regression.ipynb` | Fast, interpretable, easy to debug | Simple binary classification with a well-structured feature space |
| 🌲 **Random Forest** | `Ml_Model_for_Binary.ipynb` | Handles noisy, high-dimensional, or mixed data well | Structured queries or messier real-world inputs |

## 📁 Repository Structure

```
.
├── DistiledBert.ipynb                                  # DistilBERT-based query classifier
├── Logistic_Regression.ipynb                           # Logistic Regression baseline
├── Ml_Model_for_Binary.ipynb                            # Random Forest binary classifier
├── legal_aid_queries.csv                                # Raw legal aid query dataset
├── legal_aid_queries_processed.csv                      # Cleaned/preprocessed version of the above
├── generated_legal_queries.csv                          # Synthetic legal queries for testing
├── test_queries.csv                                     # Held-out test set
└── ILAO Generated Semantic Search Tests - Sheet1.csv    # Semantic search test cases for ILAO
```

## 🛠️ Setup

```bash
git clone https://github.com/qed42/ML_POC_ILAO.git
cd ML_POC_ILAO
pip install transformers torch scikit-learn pandas numpy
jupyter notebook
```

## ▶️ Usage

1. Open the notebook for the model you want to run — `DistiledBert.ipynb`, `Logistic_Regression.ipynb`, or `Ml_Model_for_Binary.ipynb`.
2. Run the cells top to bottom. Each notebook loads one of the CSV datasets, trains the model, and evaluates it on a held-out split.
3. To compare models like-for-like, run each notebook against the same query set (`test_queries.csv`) and compare predictions.

## 🗂️ Datasets

| File | Description |
|---|---|
| `legal_aid_queries.csv` | Original collection of legal aid queries used for training and evaluation |
| `legal_aid_queries_processed.csv` | Cleaned and normalized version of the same data, ready for model input |
| `generated_legal_queries.csv` | Synthetic queries generated to expand coverage beyond the original dataset |
| `test_queries.csv` | Held-out set used to evaluate model performance after training |
| `ILAO Generated Semantic Search Tests - Sheet1.csv` | Test cases targeting semantic search behavior for the ILAO use case |

## ⚠️ Status

This is a proof-of-concept built on dummy and synthetic data, not a production-ready classifier. Results should be treated as directional and validated against real ILAO query traffic before being used to route or filter live queries.

## 📄 License

This project is maintained by **QED42**.
