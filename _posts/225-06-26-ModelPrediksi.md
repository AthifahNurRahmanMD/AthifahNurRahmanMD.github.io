---
title: Data Mining - Prediction Model
description: Predictive Model Development for Boarding House Rental Prices in Makassar
image:
  path: "/assets/images/dataminingprojectsgroup.png"
categories: [Blogs]
tags: [Python, XGBoost Regressor, Scikit-Learn, Geopy, Matplotlib, Seaborn, Selenium, Pandas, Numpy]
---

# Predictive Model Development for Boarding House Rental Prices in Makassar Using Data Mining Techniques

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Status](https://img.shields.io/badge/Status-Completed-success.svg)]()

## 📋 Project Description

This project develops a predictive model for boarding house rental prices in Makassar City using data mining and machine learning techniques. The model aims to assist property owners in setting objective and competitive rental prices based on data analysis.

### 🎯 Research Objectives
- Identify the factors influencing boarding house rental prices in Makassar
- Build an accurate prediction model using data mining techniques
- Develop a decision support prototype for property owners

## 🏆 Main Results

- **Best Model**: XGBoost Regressor
- **Mean Absolute Error (MAE)**: Rp 219,420
- **R-squared (R²)**: 0.606 (60.6% of price variance explained)
- **Key Determinants**: AC, Sitting Toilet, Mixed Type, Location

## 📊 Dataset

- **Data Source**: Web scraping from Mamikos.com
- **Initial Data**: 1,162 listings
- **Final Data**: 562 unique listings (after duplicate cleaning)
- **Coverage**: Entire Makassar City

### Dataset Features:
- Monthly rental price
- Location (district)
- Boarding house type (male, female, mixed)
- Available facilities
- Distance to major campuses

## 🛠️ Technologies Used

### Programming Language
- **Python 3.8+**

### Main Libraries
```python
# Data Manipulation & Analysis
pandas
numpy

# Machine Learning
scikit-learn
xgboost

# Geospatial Analysis
geopy

# Web Scraping
selenium

# Visualization
matplotlib
seaborn
```

## 📁 Project Structure

```
kos-price-prediction/
│
├── data/
│   ├── raw/                    # Raw data from scraping
│   ├── processed/              # Processed data
│   └── final/                  # Final data for modeling
│
├── notebooks/
│   ├── 01_data_collection.ipynb      # Web scraping
│   ├── 02_data_preprocessing.ipynb   # Preprocessing & EDA
│   ├── 03_feature_engineering.ipynb  # Feature engineering
│   ├── 04_modeling.ipynb             # Model development
│   └── 05_evaluation.ipynb           # Model evaluation
│
├── src/
│   ├── data_collection.py      # Web scraping script
│   ├── preprocessing.py        # Data preprocessing
│   ├── feature_engineering.py  # Feature engineering
│   ├── models.py               # Model definitions
│   └── utils.py                # Utility functions
│
├── models/
│   ├── xgboost_model.pkl       # Best XGBoost model
│   └── random_forest_model.pkl # Random Forest model
│
├── dashboard/                  # Dashboard prototype
│   ├── app.py                  # Main dashboard application
│   └── static/                 # Static files
│
├── requirements.txt            # Dependencies
├── README.md                   # Documentation
<!-- └── LICENSE                     # License file -->
```

## 📈 Methodology

### 1. Data Collection
- Automated web scraping using Selenium
- Extraction from the Mamikos.com platform
- Collected 1,162 initial listings

### 2. Data Preprocessing
- Duplicate cleaning
- Handling missing values
- Data type conversion

### 3. Feature Engineering
- **Facility Encoding**: MultiLabelBinarizer for facility features
- **Boarding House Type Encoding**: One-Hot Encoding for type categories
- **Spatial Features**: Haversine distance calculation to main campuses

### 4. Outlier Handling
- Interquartile Range (IQR) method
- Upper limit = Q3 + 1.5 × IQR
- Significant performance improvement after outlier treatment

### 5. Model Development
- **Random Forest Regressor**
- **XGBoost Regressor** (Best Model)
- Data split: 80% training, 20% testing

## 📊 Evaluation Results

| Model           | MAE (Rupiah) | RMSE (Rupiah) | R-squared |
|-----------------|--------------|---------------|-----------|
| Random Forest   | 238,753      | 332,766       | 0.531     |
| **XGBoost**     | **219,420**  | **302,442**   | **0.606** |

## 🔍 Feature Importance

Based on XGBoost analysis, the top 10 factors influencing price:

1. **AC** (0.607) - Dominant factor
2. **Sitting Toilet** (0.090)
3. **Mixed Boarding House Type** (0.053)
4. **Ujung Pandang Location** (0.041)
5. **WiFi**
6. **24-Hour Access**
7. **Private Bathroom**
8. **Distance to Campus**
9. **Mattress**
10. **Rappocini Location**

## 🎯 Practical Implications

### For Property Owners:
- Objective pricing decision support tool
- Data-driven facility investment guidance
- Reduces risk of overpricing/underpricing

### For Future Research:
- Baseline model for further development
- Adaptable framework for other cities

## 🔮 Future Development

- [ ] More detailed web scraping (room size, property photos)
- [ ] Interactive dashboard with SHAP analysis
- [ ] Implementation of Neural Network (MLP model)
- [ ] More extensive hyperparameter optimization
- [ ] Real-time data integration and temporal trend analysis

## 👥 Research Team

- **Muh. Tegar Adyaksa** - *Hasanuddin University*
- **Athifah Nur Rahman MD** - *Hasanuddin University*
- **M. Ervin** - *Hasanuddin University*
- **Cholyn Sharon Enos** - *Hasanuddin University*
- **Imam Ahmad Mirza** - *Hasanuddin University*

## 🙏 Acknowledgments

Special thanks to:
- **Dr. Eng. Supri Bin Hj. Amir, S.Si., M.Eng.**
- **Octavian, S.Si., M.Kom.**

Lecturers of Data Mining Course, Hasanuddin University.

## 📚 References
1. Al Hanif, F. I., et al. (2023). "The Effect of Campus Existence on Boarding House Rental Prices"
2. Christian, Y., & Herman (2023). "Rental Price Prediction of Boarding Houses in Batam City"
3. Fitri, E. (2023). "Analisis Perbandingan Metode Regresi untuk Prediksi Harga Rumah"
4. Wisnuadhi, B., & Setiawan, I. (2021). "Rekomendasi Fitur yang Mempengaruhi Harga Sewa"

---
