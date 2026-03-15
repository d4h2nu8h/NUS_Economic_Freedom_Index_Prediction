# Economic Freedom Index Prediction — NUS × HPE Research Project

> Predicting economic freedom classifications for countries worldwide using classical machine learning and deep learning approaches, conducted as a research internship at the **National University of Singapore (NUS)** in collaboration with **Hewlett Packard Enterprise (HPE)**.

---

## 📌 Overview

Economic freedom — the degree to which individuals and businesses can make their own economic decisions — is a critical macro-level indicator used by policymakers, investors, and researchers alike. The **Index of Economic Freedom**, published annually by The Heritage Foundation, ranks countries across a wide range of economic and institutional indicators.

This project frames the prediction of a country's economic freedom **classification tier** (e.g., Free, Mostly Free, Moderately Free, Mostly Unfree, Repressed) as a supervised multi-class classification problem. Using a decade's worth of country-level data (2013–2022), we trained and evaluated **8–10 classification models** — including traditional ML algorithms and an Artificial Neural Network — to understand which features best predict a country's economic standing and how accurately we can classify it.

The project was developed during a research internship at NUS and was formally **presented to faculty professors and senior directors at Hewlett Packard Enterprise (HPE)**.

---

## 📂 Dataset

**Source:** [The Heritage Foundation — Index of Economic Freedom](https://www.heritage.org/index/)

The dataset is publicly available and spans the period **2013 to 2022**, covering countries globally across a rich set of economic, political, and institutional features including:

- Rule of Law indicators (property rights, judicial effectiveness, government integrity)
- Government size metrics (tax burden, government spending, fiscal health)
- Regulatory efficiency (business freedom, labour freedom, monetary freedom)
- Market openness (trade freedom, investment freedom, financial freedom)
- Overall economic freedom score and assigned classification tier

The dataset has been split into **three purpose-specific files** within this repository:

| File | Purpose |
|---|---|
| `Classification_Dataset.xlsx` | Raw, unprocessed data used as the original source |
| `Visualisation_Dataset.xlsx` | Cleaned subset formatted for exploratory data analysis and visualisations |
| `preprocessed_data.csv` | Feature-engineered, encoded, and scaled dataset used for model training and testing |
| `TimeSeries_Dataset.xlsx` | Temporal version of the dataset for time-aware analysis |

---

## ⚙️ Methodology

### Data Preprocessing (`Preprocessing_code.ipynb`)

- Handled missing values via mean/median imputation and forward-fill for time-series data
- Encoded categorical target labels (economic freedom tiers) using ordinal encoding
- Applied feature scaling (StandardScaler / MinMaxScaler) for distance-sensitive and gradient-based models
- Performed train-test splitting with stratification to preserve class distributions

### Models Trained (`training_and_testing.ipynb`)

The following classification algorithms were trained and benchmarked:

1. Logistic Regression
2. K-Nearest Neighbours (KNN)
3. Decision Tree Classifier
4. Random Forest Classifier
5. Gradient Boosting Classifier
6. XGBoost Classifier (`XGBOOST_predictor.ipynb`)
7. Support Vector Machine (SVM)
8. Naïve Bayes
9. Extra Trees Classifier

### Deep Learning (`ANN.ipynb`)

A feedforward **Artificial Neural Network (ANN)** was implemented separately using Keras/TensorFlow, with:

- Multiple fully-connected hidden layers with ReLU activation
- Dropout regularisation to mitigate overfitting
- Softmax output layer for multi-class classification
- Early stopping and learning rate scheduling for training stability

### Evaluation Metrics

All models were evaluated on:
- Accuracy
- Precision, Recall, F1-Score (macro and weighted)
- Confusion Matrix analysis
- ROC-AUC (one-vs-rest for multi-class)

---

## 📊 Results

The ensemble and boosting models (Random Forest, XGBoost, Gradient Boosting) consistently outperformed linear and distance-based baselines, with the tree-based ensembles demonstrating strong generalisation on held-out test data. The ANN achieved competitive performance, particularly on the larger feature-set configurations.

> **Note:** Full model score comparisons are available in `model_scores.csv` and `test_Results.py`. Refer to the individual notebooks for complete classification reports and visualisations.

---

## ⚠️ Limitations & Future Work

**Current Limitations:**
- The dataset contains a moderate class imbalance across economic freedom tiers, which may bias predictions toward majority classes
- Temporal dependencies between years are partially addressed but a full time-series forecasting approach (e.g., LSTM) could better capture year-over-year trends
- The model is trained on country-level aggregates; sub-national or regional granularity is not captured
- Some features from The Heritage Foundation involve qualitative expert assessments, introducing subjectivity into the feature space

**Future Directions:**
- Implement LSTM / Transformer-based sequence models to leverage the temporal structure of the 10-year dataset
- Apply SHAP (SHapley Additive exPlanations) values for deeper model interpretability and feature attribution
- Explore semi-supervised or transfer learning approaches to handle data-scarce years
- Extend the Streamlit dashboard with real-time predictions on newly released Heritage Foundation data

---

## 🚀 How to Run This Project

### Prerequisites

```bash
Python 3.8+
Jupyter Notebook or JupyterLab
```

### 1. Clone the Repository

```bash
git clone https://github.com/d4h2nu8h/NUS_Economic_Freedom_Index_Prediction.git
cd NUS_Economic_Freedom_Index_Prediction
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Run the Notebooks in Order

| Step | Notebook | Description |
|---|---|---|
| 1 | `Preprocessing_code.ipynb` | Data cleaning, encoding, and feature engineering |
| 2 | `training_and_testing.ipynb` | Train and evaluate all ML models (except ANN) |
| 3 | `ANN.ipynb` | Train and evaluate the Artificial Neural Network |
| 4 | `XGBOOST_predictor.ipynb` | Dedicated XGBoost training and prediction pipeline |

> All notebooks are self-contained with inline outputs. Run them sequentially for the full pipeline.

### 4. Launch the Streamlit App (Optional)

```bash
streamlit run app.py
```

---

## 🛠️ Tech Stack

| Category | Tools |
|---|---|
| **Language** | Python 3.8+ |
| **Data Manipulation** | Pandas, NumPy |
| **Machine Learning** | Scikit-learn, XGBoost |
| **Deep Learning** | TensorFlow, Keras |
| **Visualisation** | Matplotlib, Seaborn |
| **Web App** | Streamlit |
| **Notebook Environment** | Jupyter Notebook |
| **Data Format** | CSV, XLSX |

---

## 👤 Author

**Dhanush Sambasivam**
Research Intern — National University of Singapore (NUS)
*In collaboration with Hewlett Packard Enterprise (HPE)*

This project was developed as part of a formal research internship at NUS and was presented to faculty professors and senior directors at HPE.

[![GitHub](https://img.shields.io/badge/GitHub-d4h2nu8h-181717?style=flat&logo=github)](https://github.com/d4h2nu8h)

---

## 📄 License

This project is intended for academic and research purposes. The dataset is publicly available via [The Heritage Foundation](https://www.heritage.org/index/). Please cite appropriately if using this work.
