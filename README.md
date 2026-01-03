# Spark ML Churn Prediction with MLflow

End-to-end **Spark ML** project for customer churn prediction with a focus on  
**scalable feature engineering, reproducible training, and batch inference**.

This repository demonstrates how to build a **production-style machine learning pipeline** on top of Apache Spark, suitable for large-scale datasets and MLOps workflows.

---

## 1. Problem Statement

Customer churn is a critical business problem for banks and subscription-based companies.  
The goal of this project is to **predict whether a customer is likely to churn**, using historical customer behavior and profile data.

**Business value:**
- early churn detection,
- targeted retention campaigns,
- reduced revenue loss.

---

## 2. Dataset

- **Source:** Bank Churners dataset (public dataset, educational purposes)
- **Target variable:** `Attrition_Flag`
- **Task:** Binary classification (Churn / No Churn)
- **Size:** ~10k rows, ~20 features

> The dataset is used as a representative example; the pipeline is designed to scale to millions of rows without code changes.

---

## 3. Tech Stack

- Apache Spark (PySpark)
- Spark ML Pipelines
- MLflow
- Docker & Docker Compose
- Jupyter Notebook

---

## 4. Project Structure

spark-ml-flow/
│
├── notebooks/
│ ├── spark_mlib_research.ipynb # EDA and research experiments
│ └── spark_mlib_production.ipynb # Production-style batch inference
│
├── scripts/
│ ├── train.py # Spark training entrypoint
│ └── batch_score.py # Batch inference job
│
├── data/
│ ├── BankChurners.csv
│ └── README.md # Data description and license
│
├── docker/
│ └── docker-compose.yml # Spark cluster and Jupyter
│
├── requirements.txt
└── README.md

## 5. ML Pipeline Overview

The project uses **Spark ML Pipeline API** to ensure reproducibility and scalability.

**Pipeline stages:**
1. Data loading & schema validation
2. Categorical encoding (`StringIndexer`, `OneHotEncoder`)
3. Numerical feature assembly (`VectorAssembler`)
4. Model training (`LogisticRegression`)
5. Evaluation (AUC, Precision, Recall, F1)
6. Model persistence
7. Batch inference

All transformations are part of a single **PipelineModel**, ensuring consistent preprocessing during training and inference.

---

## 6. Model & Metrics

The primary model used:
- **Logistic Regression (Spark ML)**

Evaluation metrics:
- ROC-AUC
- Precision
- Recall
- F1-score

Metrics are computed using Spark evaluators to avoid driver-side bias.

Example (illustrative):

| Metric    | Value |
|----------|-------|
| ROC-AUC  | 0.85  |
| Precision| 0.78  |
| Recall   | 0.72  |
| F1       | 0.75  |

---

## 7. Experiment Tracking (MLflow)

The project is designed to integrate with **MLflow**:
- parameters (model hyperparameters),
- metrics (AUC, F1, Recall),
- artifacts (pipeline stages, evaluation reports),
- Spark `PipelineModel` logging.

This enables:
- reproducible experiments,
- model comparison,
- future model registry integration.

---

## 8. Running the Project

### 8.1 Start Spark Environment

```bash
docker compose up -d
