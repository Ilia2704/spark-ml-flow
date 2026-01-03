
---

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
