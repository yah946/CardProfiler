# Customer Segmentation and Classification Project

This project implements an intelligent customer segmentation system based on credit card usage behavior, combining unsupervised learning (clustering), supervised machine learning, experiment tracking, and a demonstration web interface.

---

## Project Structure

The project is organized in a modular way to ensure maintainability and reproducibility:

```text
customer-segmentation-project/
├── data/
│   ├── raw/               # Original dataset
│   └── processed/         # Cleaned datasets
├── notebooks/             # Exploration and prototyping notebooks
├── src/                   # Modular source code
│   ├── preprocessing.py   # Cleaning, log1p, StandardScaler, PCA
│   ├── clustering.py      # K-means, DBSCAN, validation metrics
│   ├── classification.py  # Scikit-learn pipelines, GridSearch, SMOTE
│   └── pipeline.py        # Global execution pipeline
├── models/                # Serialized pipelines (.joblib)
├── app/
│   └── app.py             # Streamlit web demonstration application
├── dags/                  # Airflow DAGs
├── mlruns/                # MLflow experiment tracking logs
├── pyproject.toml         # Project configuration and dependencies (uv)
├── uv.lock                # Locked dependency versions
└── README.md              # Technical documentation
```

---

## Installation & Reproducibility

This project uses **`uv`** for ultra-fast package management, ensuring locked and reproducible dependency versions via `uv.lock`.

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yah946/CardProfiler.git
   cd CardProfiler
   ```

2. **Install dependencies:**
   ```bash
   uv sync
   ```

---

## Project Execution

### 1. Preprocessing and Clustering
Execute the data preparation and unsupervised training scripts to generate the business target variables:
```bash
python src/preprocessing.py
python src/clustering.py
```

### 2. Supervised Classification & MLflow Tracking
Train the supervised models (Random Forest, SVM, etc.) using the unified pipeline and track your experiments with MLflow:
```bash
python src/classification.py
```

*To launch the MLflow tracking dashboard and compare runs locally:*
```bash
mlflow ui
```

### 3. Launching the Streamlit Application
Run the interactive user interface to predict new customer segments using the serialized `.joblib` pipeline:
```bash
streamlit run app/app.py
```