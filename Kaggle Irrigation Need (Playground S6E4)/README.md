# Predicting Irrigation Need: Kaggle Playground Series S6E4

**Competition page:** [Kaggle Playground Series S6E4](https://www.kaggle.com/competitions/playground-series-s6e4/overview)  
**Competition timeline:** April 1-30, 2026 

**Task:** Multiclass Classification  
**Evaluation metric:** Balanced Accuracy  

---

## Competition Description

The goal of this competition was to predict the irrigation need of agricultural plots - classified as `Low`, `Medium`, or `High` - based on a set of environmental and agricultural features. The dataset was synthetically generated from a real-world agricultural dataset, following the format of the Kaggle Playground Series which provides approachable but non-trivial problems for practising machine learning workflows. This project simulates a decision-support system designed to optimize water usage, reduce environmental waste, and ensure crop health through data-driven intervention.

---

## Competition Results

| Metric | Score |
|--------|-------|
| Private Leaderboard Score | 0.96193 |
| Final Ranking | 2,696 / 4,316 participants |
| Evaluation Metric | Balanced Accuracy |

---

## Data Summary

The dataset comprised 630,000 training observations integrating three domains of environmental data:

**1. Edaphic (Soil) Factors**
- Soil Moisture & pH: Direct indicators of immediate water availability and chemical health.
- Organic Carbon: A proxy for soil fertility and water retention capabilities.
- Electrical Conductivity: Used to monitor salinity levels, which impact osmotic pressure and plant water uptake.

**2. Meteorological & Environmental Drivers**
- Temperature (°C) & Humidity: Key predictors of the rate at which crops lose moisture to the air.
- Rainfall (mm): The primary natural water input variable.
- Sunlight Hours & Wind Speed: Secondary drivers of soil desiccation and plant stress.

**3. Agronomic & Management Context**
- Crop Type & Growth Stage: Accounts for varying water requirements of different species at different lifecycle phases.
- Season & Region: Provides the broader spatiotemporal context for the climate regime.
- Field Area & Previous Irrigation: Quantitative measures of physical scale and historical management actions.

---

## Approach & Results

Five models were developed and benchmarked in sequence, starting from a simple Decision Tree baseline and progressing through ensemble and gradient boosting methods.

| Model | Validation Accuracy | Balanced Accuracy |
|-------|:------------------:|:-----------------:|
| Decision Tree | 86.98% | 69.62% |
| Random Forest | 98.50% | 95.24% |
| LightGBM | 98.53% | 96.54% |
| XGBoost | 98.53% | 96.43% |
| CatBoost | 98.53% | 96.29% |

LightGBM achieved the highest balanced accuracy and was selected for the final submission.

---

## Methodology

The project follows a deliberate benchmarking methodology, progressing from a simple interpretable baseline through increasingly sophisticated models to understand precisely where and why performance gains occur.

**Decision Tree:** Trained with a maximum depth of four to limit overfitting. One-hot encoding was applied to categorical features using `pd.get_dummies()`. Achieved a validation accuracy of 86.98%, establishing a performance floor against which all subsequent models are measured.

**Random Forest:** First ensemble method, aggregating predictions across 100 decision trees each trained on a random subset of the data. Produced the largest single performance jump of the entire project, an 11.5 percentage point gain to 98.50% validation accuracy, demonstrating the power of bagging-based ensemble averaging over a single tree.

**LightGBM:** First gradient boosting model, leveraging its native handling of categorical features via target encoding and sequential tree construction. Achieved the highest balanced accuracy of 96.54% (the official competition metric) providing the most meaningful benchmark against the Kaggle leaderboard.

**XGBoost:** Trained with 1,000 estimators, early stopping at 50 rounds, a learning rate of 0.05, and stochastic subsampling of rows and features to reduce overfitting. Achieved the highest raw validation accuracy of 98.54% and a balanced accuracy of 96.48%.

**CatBoost:** Chosen for its native categorical feature handling via ordered boosting without any manual preprocessing. Converged at iteration 161 of 1,000 (the earliest stopping point of any boosting model) achieving a validation accuracy of 98.53% and demonstrating efficient generalisation on this dataset's feature set.

---

## Key Techniques

- Label encoding and target encoding for categorical features.
- Stratified train/validation splitting to preserve class balance.
- Early stopping for all gradient boosting models.
- Confusion matrix and feature importance analysis per model.
- Balanced accuracy evaluation as the primary competition metric.

---

## Figures

| Figure | Description |
|--------|-------------|
| `model_comparison_full.png` | Validation accuracy vs balanced accuracy across all models |
| `decision_tree_confusion_matrix.png` | Decision Tree confusion matrix |
| `decision_tree_feature_importance.png` | Decision Tree feature importances |
| `random_forest_confusion_matrix.png` | Random Forest confusion matrix |
| `random_forest_feature_importance.png` | Random Forest feature importances |
| `LGBM_confusion_matrix.png` | LightGBM confusion matrix |
| `LGBT_feature_importance.png` | LightGBM feature importances |
| `xgboost_confmatrix_featimportance.png` | XGBoost confusion matrix and feature importances |
| `catboost_confmatrix_featimportance.png` | CatBoost confusion matrix and feature importances |

---

## Files

| File | Description |
|------|-------------|
| `Kaggle_IrrigationNeed_ML.ipynb` | Full modelling notebook |

---

## Skills & Tools Demonstrated

Python · scikit-learn · XGBoost · LightGBM · CatBoost · pandas · matplotlib · Multiclass classification · Ensemble methods · Gradient boosting · Feature encoding · Label encoding · Stratified train-validation splitting · Early stopping · Balanced accuracy evaluation · Kaggle competition workflow · Jupyter Notebook

---

## Further Reading

Full write-up available on my [ePortfolio](https://sites.google.com/view/jessicamiddleton-eportfolio/kaggle-competitions/predicting-irrigation-need).
