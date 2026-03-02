# 🚕 Machine Learning Analysis of NYC Taxi Trip Data

## 📘 Module Information
- **Module Code:** 7006SCN – Machine Learning and Big Data – 2526JANMAR  
- **Course:** MSc Data Science  
- **Student:** Ashish  
- **Dataset:** NYC TLC Yellow Taxi Trip Records (2019)

---

## 📌 Project Overview

This project builds a **scalable distributed machine learning pipeline** using **Apache Spark** to predict taxi fares from large-scale trip data.

The dataset contains:

- **84,598,444 records**
- **1.15 GB size**
- **19 raw features**

Due to the scale of data, distributed processing was required. The system was designed to evaluate both **predictive performance** and **scalability behaviour**.

---

## 🏗 System Architecture

A two-layer architecture was implemented:

### 🔹 Bronze Layer (Data Ingestion)
- Distributed loading of Parquet files
- Schema validation
- Partition management
- Null-value analysis
- Stored as structured checkpoint dataset

### 🔹 Silver Layer (Feature Engineering)
- Removal of corrupted records
- Creation of engineered features:
  - `trip_duration`
  - `pickup_hour`
  - `is_weekend`
- Reduced cardinality of location features
- Final selection of **9 predictive features**

---

## 🤖 Models Implemented

The following regression models were trained using **Spark MLlib**:

- Linear Regression
- Decision Tree
- Random Forest
- Gradient Boosted Trees (GBT)

A **time-aware train-test split** was applied to prevent data leakage.

---

## 📊 Model Performance (RMSE)

| Model | RMSE |
|--------|--------|
| Linear Regression | 12.56 |
| Decision Tree | 14.97 |
| Random Forest | 4.52 |
| Random Forest (Tuned) | 4.92 |
| **Gradient Boosted Trees** | **3.53** |

### Key Insight:
Ensemble tree-based methods significantly outperform linear models, confirming strong non-linear relationships in taxi fare data.

---

## 🔬 Advanced Validation Techniques

- Bootstrap Confidence Interval for RMSE
- 3-fold Cross-Validation (Hyperparameter Tuning)
- Feature Importance Analysis
- Strong Scaling Experiments
- Weak Scaling Experiments
- MLflow experiment tracking for reproducibility

---

## 📈 Scalability Experiments

### 🔹 Strong Scaling
- Fixed data size
- Increased shuffle partitions (50, 100, 200)
- Observed scheduling overhead beyond optimal range

### 🔹 Weak Scaling
- Increased data fractions (0.1, 0.3, 0.6)
- Runtime increased proportionally
- Demonstrated stable distributed scaling behaviour

---

## 📊 Tableau Visualisations

The following dashboards were created:

- Model Predictions (Actual vs Predicted)
- Residual Distribution (GBT)
- Feature Importance
- Strong Scaling
- Weak Scaling

---

## 🛠 Technologies Used

- Apache Spark
- PySpark MLlib
- MLflow
- Pandas
- Scikit-Learn (comparison experiment)
- Tableau

---

## ⚠ Limitations

- GBT trained on 5% sample due to computational constraints.
- External data (traffic, weather) not included.
- Hyperparameter tuning limited by runtime.

---

## 🚀 Future Improvements

- Train GBT on full dataset with optimized cluster.
- Evaluate XGBoost / LightGBM.
- Incorporate external traffic & weather features.
- Deploy using Spark Structured Streaming for real-time prediction.

---


---

## 🧠 Conclusion

This project demonstrates:

- Large-scale distributed data engineering
- Ensemble-based non-linear regression modelling
- Reproducible ML experimentation
- Practical scalability analysis

Apache Spark proved to be an effective and robust framework for handling large-scale machine learning workflows.
