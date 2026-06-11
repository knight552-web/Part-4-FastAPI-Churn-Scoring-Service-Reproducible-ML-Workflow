# Customer Churn Prediction API

## Overview

This project deploys the customer churn prediction model developed in Part 3 as a FastAPI application.

The API allows users to submit customer behavioral and profile information and receive:

- Churn probability
- Predicted churn class
- Risk level
- Risk explanation

The model used is a Logistic Regression classifier trained to predict whether a customer will churn within the next 60 days.

## Files Included

- main.py
- test_api.py
- model.pkl
- requirements.txt
- monitoring_plan.md
- responsible_use.md
- README.md

## API Endpoints

### GET /health
Returns API health status.

### POST /predict
Predict churn risk for a single customer.

### POST /batch_predict
Predict churn risk for multiple customers.

## Installation

```bash
pip install -r requirements.txt
```

## Running the API

```bash
uvicorn main:app --reload
```

## API Documentation

Open:

http://127.0.0.1:8000/docs

## Running Tests

```bash
pytest test_api.py
```
