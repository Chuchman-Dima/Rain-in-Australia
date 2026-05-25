# 🌧️ Rain in Australia — Prediction

Kaggle competition project to predict next-day rain in Australia based on current weather data.

## 📋 Overview

This project implements a machine learning solution to predict whether it will rain tomorrow in Australian cities using historical weather data. The dataset contains 145,460 observations across 23 weather features collected from various Australian locations.

**Target Variable:** `RainTomorrow` — Binary classification (Yes/No)

## 📊 Dataset Statistics

| Metric | Value |
|--------|-------|
| Total Records | 145,460 |
| Features | 23 |
| Locations | Multiple Australian cities |
| Date Range | 2008-2010 |
| Class Distribution | No: 77.8% / Yes: 22.2% |

### Missing Data

| Feature | Missing (%) |
|---------|-------------|
| Sunshine | 48.01% |
| Evaporation | 43.17% |
| Cloud3pm | 40.81% |
| Cloud9am | 38.42% |
| Pressure9am/3pm | ~10.3% |
| WindDir/WindGustDir | ~7% |
| Other features | <5% |

## 🔍 Key Features

### Weather Variables
- **Temperature**: MinTemp, MaxTemp, Temp9am, Temp3pm
- **Humidity**: Humidity9am, Humidity3pm
- **Pressure**: Pressure9am, Pressure3pm
- **Wind**: WindGustDir, WindGustSpeed, WindDir9am, WindDir3pm, WindSpeed9am, WindSpeed3pm
- **Precipitation**: Rainfall, Evaporation, Sunshine
- **Clouds**: Cloud9am, Cloud3pm
- **Historical**: RainToday
- **Location**: Location, Date (converted to Month)

## 📈 Project Structure

```
Rain-in-Australia/
├── Rain in Australia.ipynb    # Main analysis notebook
├── weatherAUS.csv             # Weather dataset
└── README.md                  # This file
```

## 🛠️ Methodology

### 1. **Data Loading & EDA**
- Loaded 145,460 records from weatherAUS.csv
- Analyzed missing values distribution
- Visualized target variable distribution and feature relationships

### 2. **Feature Engineering**
- Extracted month from date
- Encoded categorical variables (Location, WindGustDir, WindDir9am, WindDir3pm, RainToday)
- Target encoding: Yes→1, No→0

### 3. **Data Preprocessing**
- Imputation strategy:
  - **Numerical features**: Median imputation
  - **Categorical features**: Most frequent value imputation
- Label encoding for categorical variables
- No missing values after preprocessing (verified: 0 nulls)

### 4. **Exploratory Data Analysis**

**Key Insights:**
- Strong correlation between humidity levels and rain (higher humidity → higher rain probability)
- Maximum temperature inversely correlated with rain
- Class imbalance: ~78% No Rain vs 22% Rain Tomorrow
- Pressure and humidity at 3pm are strong predictors

### 5. **Model Training**
- Train-test split (default: 80-20)
- Standardized features (StandardScaler)
- Models implemented:
  - **Random Forest Classifier** — Ensemble method for robustness
  - **Logistic Regression** — Baseline linear model

### 6. **Model Evaluation**
- Metrics:
  - Classification Report (Precision, Recall, F1-Score)
  - Confusion Matrix
  - ROC-AUC Score
  - ROC Curve

## 📊 Results

### Feature Importance (Expected)
Top predictors for rain tomorrow:
1. Humidity levels (9am & 3pm)
2. Pressure (9am & 3pm)
3. Maximum temperature
4. Rainfall today
5. Cloud coverage

### Performance Metrics
- Both models tested on balanced and imbalanced datasets
- ROC-AUC used as primary metric due to class imbalance
- Random Forest typically outperforms Logistic Regression

## 🚀 Quick Start

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

### Run the Analysis
```bash
jupyter notebook "Rain in Australia.ipynb"
```

The notebook will:
1. Load and explore the dataset
2. Perform data preprocessing
3. Create visualizations
4. Train models
5. Display performance metrics

## 📌 Key Findings

✅ **High-confidence predictors:**
- Humidity3pm (strongest predictor)
- Pressure metrics
- Temperature range (MinTemp, MaxTemp)
- RainToday (historical pattern)

⚠️ **Data Quality Issues:**
- 48% missing values in Sunshine
- 43% missing values in Evaporation
- These features dropped/imputed during preprocessing

## 🔮 Future Improvements

- [ ] Feature engineering: rolling averages, seasonal patterns
- [ ] Hyperparameter tuning (GridSearchCV, RandomizedSearchCV)
- [ ] Advanced models: XGBoost, LightGBM, Neural Networks
- [ ] SMOTE for handling class imbalance
- [ ] Cross-validation strategies (StratifiedKFold)
- [ ] Feature selection optimization
- [ ] Location-specific models
- [ ] Time-series considerations

## 📝 Notebook Sections

1. **Imports** — Required libraries
2. **Data Loading** — CSV import and shape verification
3. **EDA** — Descriptive statistics and visualizations
4. **Preprocessing** — Missing value handling and encoding
5. **Model Training** — Random Forest and Logistic Regression
6. **Evaluation** — Performance metrics and ROC curves
7. **Analysis** — Feature importance and insights

## 🌍 Dataset Information

**Source:** Kaggle - [Rain in Australia](https://www.kaggle.com/jsphyg/weather-dataset-rattle-package)

**Locations Covered:** Major Australian cities
- Albury, BadgerysCreek, Cobar, Canberra, Dartmouth, and many others

**Date Range:** 2007-2017 (with focus on 2008-2010 in this analysis)

## 👤 Author

**Dima Chuchman**

## 📄 License

This project is for educational and competition purposes.

---

**Last Updated:** 2026-05-25  
**Status:** Active Development
