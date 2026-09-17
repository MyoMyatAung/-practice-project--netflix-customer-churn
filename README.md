# Netflix Customer Churn & Engagement Analysis

A practice project exploring subscriber churn on a synthetic Netflix-style dataset — user engagement, billing, and account activity — to uncover behavioral signals that precede churn.

## Business Problem

Acquiring a new customer typically costs 5–7x more than retaining an existing one. This project digs into subscriber engagement, hardware usage, billing, and inactivity patterns to explore:

1. **Early attrition indicators** — behavioral signals (login inactivity, declining watch hours) that predict churn
2. **Subscription tier viability** — how churn rates differ across Basic, Standard, and Premium plans
3. **Regional & demographic dynamics** — which markets and age cohorts carry the highest retention/attrition risk
4. **Payment gateway friction** — whether payment method correlates with churn

## Dataset

`data/netflix_customer_churn.csv` — 5,000 rows, 14 columns, one row per subscriber.

| Column | Description |
|---|---|
| `customer_id` | Unique subscriber identifier |
| `age` | Subscriber age |
| `gender` | Subscriber gender |
| `subscription_type` | Basic / Standard / Premium |
| `watch_hours` | Total hours watched |
| `last_login_days` | Days since last login |
| `region` | Geographic region |
| `device` | Primary streaming device |
| `monthly_fee` | Monthly subscription fee (maps 1:1 to `subscription_type`) |
| `churned` | Target variable — 1 if the subscriber churned, else 0 |
| `payment_method` | Billing/payment method |
| `number_of_profiles` | Number of profiles on the account |
| `avg_watch_time_per_day` | Average daily watch time |
| `favorite_genre` | Most-watched genre |

## Contents

- [`customer-churn.ipynb`](customer-churn.ipynb) — main analysis notebook:
  - Initial data inspection (structure, value counts, distributions)
  - Stratified train/test split (stratified on churn and quantile bins of the skewed watch-time features, validated with KS-tests)
  - Univariate exploratory data analysis on numerical features

## Setup

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook customer-churn.ipynb
```

## Requirements

See [`requirements.txt`](requirements.txt): numpy, pandas, matplotlib, seaborn, scikit-learn, jupyter.

## Status

Work in progress — EDA is underway; classification modeling (churn prediction), feature importance, and customer segmentation are planned next steps.
