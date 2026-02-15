# British-airways-job-simulation-from-forage
Done virtual internship of British Airways from forage platform

## Airport Planning & Customer Analytics Project

This repository contains solutions for the British Airways Virtual Experience Program, focusing on **customer analytics and airport lounge demand forecasting**.



# 📌 Task 1 – Lounge Eligibility Demand Forecasting

## 🎯 Objective

Create a scalable lookup model to estimate **lounge access eligibility percentages** across flight groupings at Heathrow Terminal 3.

Since future schedules are uncertain, the model must:

* Be flexible
* Not depend on exact aircraft configuration
* Work across different route types



## 🏢 Business Context

Lounge access depends on:

* Cabin class (Business/First)
* Loyalty tier
* Route type (Short vs Long haul)

BA needs a simple model to:

* Estimate daily lounge load
* Plan capacity
* Optimize resource allocation



## 🧠 Modeling Strategy

Flights were grouped by:

* Haul Type (Short / Long)
* Travel patterns
* Passenger mix assumptions

Reasoning:

* Short haul → Higher Tier 3 loyalty travelers
* Long haul → More premium cabin passengers
* Arrival region highly correlated with haul → not included separately


## 📊 Final Lookup Table

| Haul Type  | Tier 1 % | Tier 2 % | Tier 3 % |
| ---------- | -------- | -------- | -------- |
| Long Haul  | 0.22%    | 2.92%    | 11.13%   |
| Short Haul | 0.34%    | 4.40%    | 16.85%   |


## 📝 Assumptions

* Loyalty tiers derived from historical distribution
* Haul strongly influences premium mix
* Arrival region excluded due to multicollinearity
* Designed for scalability under schedule uncertainty


## 💼 Business Impact

This lookup table allows BA to:

* Estimate lounge demand without aircraft-level data
* Model different scheduling scenarios
* Identify capacity stress points
* Support infrastructure investment decisions



# 🛠 Tools Used

* Python (Pandas, Scikit-learn)
* Power BI
* Data Visualization
* Business Reasoning & Assumption Modeling


# 🚀 Key Skills Demonstrated

* Business-driven data analysis
* Predictive modeling
* Feature engineering
* Model evaluation (ROC, Recall, CV)
* Forecasting using assumption-based modeling
* Translating analytics into operational decisions


# 📌 Task 2 – Customer Booking Prediction Model

## 🎯 Objective

Build a predictive model to identify whether a customer will complete a booking.

The goal is to help British Airways:

* Improve marketing efficiency
* Reduce unnecessary promotional costs
* Target high-conversion customers


## 📊 Business Problem

Not all website visitors complete bookings.
BA wants to:

* Identify high-probability customers
* Optimize promotional spend
* Improve revenue conversion rates


## 🧠 Approach

### 1️⃣ Data Preprocessing

* Cleaned missing values
* Encoded categorical variables
* Created meaningful features (e.g., flight time bucket, origin region)
* Handled class imbalance using stratified sampling

### 2️⃣ Feature Engineering

Important drivers identified:

* Purchase lead time
* Length of stay
* Origin region (SE Asia, Oceania)
* Flight duration
* Number of passengers
* Add-ons selected

### 3️⃣ Model Used

* Random Forest Classifier
* Stratified Cross-Validation


## 📈 Model Performance

| Metric                   | Value         |
| ------------------------ | ------------- |
| ROC-AUC                  | 0.76          |
| Recall (Threshold = 0.4) | 61%           |
| Precision                | 31%           |
| CV AUC                   | 0.756 ± 0.004 |

### 🔍 Interpretation

* Strong separation between buyers and non-buyers
* 61% of actual buyers correctly identified
* Enables smarter promotion targeting
* Reduces waste in blanket discount campaigns


## 💼 Business Impact

If deployed, BA can:

* Target high-intent users
* Reduce marketing spend
* Increase booking conversion rate
* Personalize offers based on region & travel pattern
