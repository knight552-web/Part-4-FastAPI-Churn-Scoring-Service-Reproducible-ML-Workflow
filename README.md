# Customer Churn Prediction API

## Project Overview

This project deploys a customer churn prediction model as a FastAPI application.

The API predicts whether a customer is likely to churn within the next 60 days based on customer profile information, purchase behavior, support interactions, and engagement metrics.

The deployed model is a Logistic Regression classifier trained during Part 3 of the project and configured with an optimized decision threshold of 0.45.

The API provides:

* Churn probability
* Predicted churn class
* Risk level (Low, Medium, High)
* Risk explanation

---

# Project Files

```text
main.py
test_api.py
model.pkl
requirements.txt
monitoring_plan.md
responsible_use.md
README.md
```

---

# Setup Instructions

## Step 1: Clone or Download the Project

Place all project files in the same directory.

Required files:

```text
main.py
model.pkl
requirements.txt
```

---

## Step 2: Install Dependencies

Run:

```bash
pip install -r requirements.txt
```

---

# Running the API

Start the FastAPI application using:

```bash
uvicorn main:app --reload
```

Explanation:

* `main` refers to `main.py`
* `app` refers to the FastAPI application object
* `--reload` automatically reloads the server when changes are detected

Successful startup should display:

```text
INFO: Uvicorn running on http://127.0.0.1:8000
```

---

# API Documentation

FastAPI automatically generates interactive Swagger documentation.

Open:

```text
http://127.0.0.1:8000/docs
```

This interface allows all endpoints to be tested directly from a browser.

---

# Endpoint Details

## GET /health

### Purpose

Verify that the API is running correctly.

### Example Response

```json
{
  "status": "healthy"
}
```

---

## POST /predict

### Purpose

Generate a churn prediction for a single customer.

### Input

Customer behavioral and profile attributes.

### Example Request

```json
{
  "recency_days": 120,
  "frequency_180d": 2,
  "monetary_180d": 1000,
  "return_rate_180d": 0.10,
  "avg_discount_pct_180d": 0.30,
  "avg_rating_180d": 4.0,
  "category_diversity_180d": 2,
  "ticket_count_90d": 1,
  "negative_ticket_rate_90d": 0.20,
  "avg_resolution_hours_90d": 20,
  "days_since_signup": 400,
  "sessions_30d": 5,
  "product_views_30d": 10,
  "cart_adds_30d": 3,
  "wishlist_adds_30d": 1,
  "abandoned_carts_30d": 2,
  "email_opens_30d": 1,
  "campaign_clicks_30d": 0,
  "last_visit_days_ago": 20,
  "city_tier": "Tier 1",
  "age_group": "25-34",
  "acquisition_channel": "Organic",
  "loyalty_tier": "Gold",
  "preferred_category": "Skin Care",
  "marketing_consent": "Yes"
}
```

### Example Response

```json
{
  "churn_probability": 0.585,
  "predicted_class": 1,
  "risk_level": "Medium",
  "risk_explanation": "negative support interactions, heavy discount dependency"
}
```

---

## POST /batch_predict

### Purpose

Generate predictions for multiple customers within a single request.

### Output

Returns a list of prediction objects.

---

# Running Tests

API tests are implemented in:

```text
test_api.py
```

Execute tests using:

```bash
pytest test_api.py
```

Expected output:

```text
====================
4 passed
====================
```

The test suite validates:

* Health endpoint functionality
* High-risk prediction scenario
* Low-risk prediction scenario
* Batch prediction endpoint

---

# Model Notes

## Model Type

Logistic Regression

## Decision Threshold

0.45

## Test Performance

| Metric    |  Score |
| --------- | -----: |
| Accuracy  | 80.95% |
| Precision | 79.55% |
| Recall    | 83.33% |
| F1 Score  | 81.40% |
| ROC-AUC   | 88.58% |

---

# Source Data Notes

The model was trained using the provided churn modeling dataset (`rfm_modeling_snapshot.csv`).

Features include:

* Customer purchase behavior
* RFM metrics
* Support interactions
* Website engagement
* Loyalty information
* Marketing engagement

The target variable predicts whether a customer will churn within the next 60 days.

The dataset was split into:

* Train
* Validation
* Test

The validation set was used for threshold optimization and model selection, while the final performance was evaluated on the unseen test set.

---

# Additional Documentation

Additional deployment and governance documentation is provided in:

```text
monitoring_plan.md
responsible_use.md
```

These documents describe production monitoring requirements, retraining triggers, and responsible use guidelines for business teams.
