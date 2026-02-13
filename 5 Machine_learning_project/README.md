# 🔋 Predicting Electric Vehicle User Types Using Machine Learning

**Course Project — Data Mining / Machine Learning**  
**Author:** Nikhil Chhatraband  

---

## 🚀 Project Overview

This project builds a multiclass machine learning model to predict **Electric Vehicle (EV) user types** based on charging session data.

Target Variable:
- **User Type** (Commuter, Casual Driver, Long-Distance Traveler)

The motivation behind this project is to support smarter EV infrastructure planning by understanding behavioral patterns of different charging users.

---

## 📊 Dataset Description

- Source: Kaggle
- 1,320 charging session records
- 20 features (10 numerical, 10 categorical)
- Each row represents one EV charging session

### Feature Examples:
- Battery Capacity
- Charging Duration
- Energy Consumed (kWh)
- Charging Rate (kW)
- Distance Driven
- Time of Day
- Day of Week
- Charger Type
- Temperature

This dataset reflects real-world EV charging behavior in the sustainability and transportation domain.

---

## 🔍 Exploratory Data Analysis (EDA)

Key Findings:

- No strong linear correlation (|r| > 0.3) with charging duration
- Mild class imbalance (most users labeled as Commuter)
- Long-Distance Travelers:
  - Higher charging duration
  - Higher energy consumption
- Time-of-day behavior varies by user type

Visualizations included:
- Correlation heatmap
- Histograms & boxplots
- Class distribution plots

---

## 🛠 Data Preprocessing

A consistent preprocessing pipeline was implemented using **ColumnTransformer**:

### Numerical Features:
- Mean imputation
- Standardization (scaling)

### Categorical Features:
- Mode imputation
- One-hot encoding

### Columns Removed:
- User ID
- Timestamps
- Location data (to prevent leakage)

### Data Split:
- 60% Training
- 20% Validation
- 20% Test

No SMOTE applied (class imbalance not severe).

---

## 🤖 Models Trained

Six classification models were trained and evaluated:

| Model | Accuracy | F1 Score | Key Parameters |
|--------|----------|----------|----------------|
| Logistic Regression | 0.758 | 0.751 | C=0.1 |
| Decision Tree | 0.708 | 0.704 | max_depth=10 |
| Random Forest | 0.788 | 0.781 | n_estimators=100 |
| Gradient Boosting | ⭐ 0.792 | ⭐ 0.787 | Early stopping |
| SVM (SVC) | 0.774 | 0.765 | C=1.0 |
| Neural Network (MLP) | 0.770 | 0.760 | (100, 50) layers |

---

## 🏆 Best Model

**Gradient Boosting**
- Highest Accuracy and F1 Score
- Stable performance
- Efficient with early stopping

Random Forest also performed strongly and provided useful feature importance insights.

---

## 📈 Key Insights

### 🔑 Top Predictive Features:
- Charging Duration
- State of Charge
- Energy Consumed

### ⚠️ Confusion Matrix (SVM):
- Confusion between Casual Driver and Commuter
- Indicates overlapping charging behavior

These insights can help:
- Dynamic pricing strategies
- Infrastructure load balancing
- Charging station placement optimization

---

## 🧠 Business Impact

This model can help:
- EV infrastructure companies anticipate demand
- Utilities optimize energy distribution
- Smart city planners allocate resources effectively

---

## 🔮 Future Improvements

- Add cyclic encoding for Time of Day
- Apply SMOTE for class balancing
- Hyperparameter tuning for neural networks
- Ensemble voting / model stacking
- Integrate geolocation or weather data

---

## 📁 Project Structure

