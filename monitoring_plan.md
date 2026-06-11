# Monitoring Plan

## Objective

Monitor the churn prediction API to ensure accuracy, reliability, and business value after deployment.

## 1. Data Drift Monitoring

Monitor:
- recency_days
- frequency_180d
- monetary_180d
- return_rate_180d
- sessions_30d
- negative_ticket_rate_90d

Frequency: Weekly

## 2. Prediction Distribution Monitoring

Track:
- Average churn probability
- Percentage of High Risk customers
- Percentage of Medium Risk customers
- Percentage of Low Risk customers

Frequency: Daily

## 3. Business Outcome Monitoring

Track:
- Actual churn rate
- Retention campaign success rate
- Revenue retained
- Churn rate by risk level

Frequency: Monthly

## 4. API Reliability Monitoring

Track:
- Uptime
- Response latency
- Request volume
- Error rates

Frequency: Continuous

## 5. Retraining Triggers

Retrain when:
- ROC-AUC declines significantly
- Feature drift becomes substantial
- Customer behavior changes materially
- Prediction quality degrades

Recommended review cycle: Quarterly.
