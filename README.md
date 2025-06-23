# Rainfall Prediction Classifier — IBM Machine Learning Project (Coursera)

This is a supervised machine learning project completed as part of the [IBM Machine Learning with Python course on Coursera](https://www.coursera.org/learn/machine-learning-with-python). The objective is to build a predictive model that can determine **whether it will rain today** based on historical weather data in the **Melbourne region**.

---

## Problem Statement

Accurate rainfall prediction is essential for daily decision-making in agriculture, transportation, and city planning. This project focuses on creating a binary classifier that can **predict if it will rain today** using only weather features available **up to and including yesterday**, avoiding future data leakage.

---

## Project Objectives

- Explore and clean a real-world weather dataset
- Perform feature engineering (e.g., extracting seasonality)
- Build a scikit-learn pipeline for preprocessing and modeling
- Train and tune both Random Forest and Logistic Regression classifiers
- Evaluate model performance using precision, recall, F1-score, and accuracy
- Extract and visualize feature importances
- Compare models based on their ability to detect rainy days

---

## Dataset Overview

The dataset contains daily weather observations across various Australian locations from **2008 to 2017**. After filtering for only **Melbourne, MelbourneAirport, and Watsonia**, the following features were used:

| Field           | Description                                     |
|----------------|-------------------------------------------------|
| Date           | Date of observation                             |
| MinTemp        | Minimum temperature (°C)                         |
| MaxTemp        | Maximum temperature (°C)                         |
| Rainfall       | Amount of rainfall (mm)                          |
| Sunshine       | Sunshine duration (hours)                        |
| WindGustSpeed  | Speed of the strongest wind gust (km/h)          |
| WindDir        | Wind direction (categorical)                     |
| Pressure9am/3pm| Atmospheric pressure (hPa)                       |
| Humidity9am/3pm| Relative humidity (%)                            |
| Temp9am/3pm    | Temperature readings (°C)                        |
| RainYesterday  | Whether it rained the previous day (Yes/No)     |
| RainToday      | Target: Whether it rained today (Yes/No)      |
| Season         | Extracted from date (Summer, Autumn, etc.)      |
| Location       | Categorical (only 3 cities used)                 |

---

## Machine Learning Workflow

### Preprocessing
- Dropped rows with missing values
- Renamed columns to prevent target leakage
- Filtered for localized Melbourne region
- Created a `Season` feature from `Date`
- One-hot encoded categorical features
- Standard scaled numeric features

### Class Balance

- **RainToday = No**: 5,766 observations (~76%)
- **RainToday = Yes**: 1,791 observations (~24%)
- Stratified split used to maintain class proportions

### Models Trained

1. **Random Forest Classifier**
2. **Logistic Regression**

Both models were:
- Trained using a full pipeline (preprocessing + classifier)
- Tuned using `GridSearchCV` with 5-fold stratified cross-validation

---

## Results Summary

### Random Forest Classifier

- **Accuracy**: 84.5%
- **True Positive Rate (Rain Recall)**: 50%
- **Top Features**: Humidity3pm, Pressure3pm, Sunshine

### Logistic Regression

- **Accuracy**: 83.0%
- **True Positive Rate (Rain Recall)**: 51%
- Slightly better recall, but slightly worse accuracy than Random Forest

---

## Feature Importances

Top features influencing rain prediction:

- **Humidity3pm** (~12%)
- **Pressure3pm** (~8.8%)
- **Sunshine**, **WindGustSpeed**, **MaxTemp**
- Categorical features had lower importance compared to numeric ones

---

## Final Takeaways

- **Random Forest** is more accurate and robust overall
- **Logistic Regression** offers better interpretability and recall
- Afternoon humidity and pressure are strong indicators of rainfall
- A realistic model must avoid future leakage by only using past and current-day features

---

## Future Improvements

- Apply SMOTE or class weights to handle class imbalance
- Adjust decision thresholds to improve rainy-day recall
- Use more complete data (with imputation instead of dropna)
- Try other classifiers like XGBoost, SVM, or stacking ensembles

---

## File Structure

```
Rainfall-Prediction-Classifier-IBM-ML-Coursera
├── Rainfall_Prediction_Classifier.ipynb   # Final notebook
├── README.md                              # Project overview
└── data/
    └── weatherAUS.csv                     # Original dataset
```
---

## Course Information

**Course**: [Machine Learning with Python](https://www.coursera.org/learn/machine-learning-with-python)  
**Platform**: Coursera  
**Provided by**: IBM  
**Duration**: ~20 hours  
**Certificate**: [View Certificate](https://www.coursera.org/account/accomplishments/records/AL9M7Z86VTQG) 

---

## Author

**Zeeshan Akram**  
BS Software Engineering | Data Science Enthusiast  
[LinkedIn](https://www.linkedin.com/in/zeeshan-akram-572bbb34a/) | [GitHub](https://github.com/zeeshan-akram-ds)

---

## License

This project is part of an educational course and provided for learning purposes only.
