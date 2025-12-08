# Assignment 3 - Data Analytics (WS25)
### Mobile Price Classification Using CRISP-DM & PROV-O Documentation  
**Authors:** Muhammad Ibrar & Ahmad Ibrahim  



## Project Overview

This project applies the **CRISP-DM** methodology to classify mobile phones into four price ranges (0-3) based on their technical specifications.  
All analytical steps are accompanied by **PROV-O provenance tracking** and dataset documentation using **Schema.org** and **Croissant**.

Dataset used:  
**Mobile Price Classification** - https://www.kaggle.com/datasets/iabhishekofficial/mobile-price-classification

Currently completed phases:

- **Phase 1 - Business Understanding**   
- **Phase 2 - Data Understanding**   
- **Phase 3 - Data Preparation**   

The next phase will begin: **Modeling**.



## 1. Business Understanding (Completed)

This phase defines the project motivation and goals:

- **Scenario:** A new mobile company aims to understand how device features drive price range to support competitive pricing.
- **Business Objectives:** Predict the mobile phone price range class using device attributes.
- **Business Success Criteria:** Achieve ≥ 85% accuracy and provide interpretable insights for product strategy.
- **Data Mining Goals:** Build and compare ML models (SVM, Decision Tree, Random Forest).
- **AI Risk Considerations:** Bias, minority device types, unclear feature semantics.

All elements were logged using **PROV-O entities and associations**.



## 2. Data Understanding (Completed)

###  Dataset structure documented using Schema.org & Croissant  
###  Exploratory Data Analysis includes:

- Attribute types, semantics, distributions  
- Summary statistics (numerical + categorical)  
- Categorical feature distributions (pie charts)  
- Numerical feature distributions (histograms)  
- Correlation heatmap  
- Outlier detection (primarily in `fc`)  
- Noise detection (`sc_w < 2`, `px_height < 5`)  
- Data quality assessment (no missing values, no duplicates)

### Key Findings:

- Dataset is clean, complete, and balanced across all four target classes.
- RAM shows strong correlation with price_range (ρ = 0.92).
- Some noise-like values exist but could reflect older device models.
- Outliers were found but not removed due to domain uncertainty.

All analyses were documented using **PROV-O Activities**.



## 3. Data Preparation (Completed)

###  Quality checks performed:

- Duplicate detection  
- Missing value check  
- Outlier identification  
- Noise tagging  
- Data quality summary (with provenance)

###  Preprocessing actions considered but not applied:

- No global scaling (will be applied only in SVM pipeline)
- No binning (not needed for balanced continuous data)
- No encoding (categorical features already numeric)
- No noise removal (values may represent valid older devices)
- No outlier removal (insufficient justification)
- No feature removal based solely on Pearson correlation

###  Additional documentation:

- Potential derived attributes: screen area, pixel density, camera score, etc.  
- Potential external data sources: market prices, device catalogs, manufacturer specs

###  Prepared Dataset:

Since no destructive preprocessing was applied, the prepared dataset is identical to the loaded dataset but documented as `:prepared_data` in the provenance graph.



## Project Status

| CRISP-DM Phase | Status | Notes |
|-|--|-|
| **Business Understanding** | Completed | Fully documented with PROV-O |
| **Data Understanding** | Completed | Includes EDA, correlation, outlier/noise detection |
| **Data Preparation** | Completed | No destructive transformations required |
| **Modeling** | Not started | Next phase |
| **Evaluation** | Pending | After modeling |
| **Deployment** | Not part of assignment | |



## Next Steps

Upcoming **Modeling Phase** will include:

- Train-test split  
- Model pipelines (scaling for SVM only)  
- Base models (SVM, Decision Tree, Random Forest)  
- Hyperparameter tuning  
- Performance evaluation (accuracy + macro metrics)  
- Provenance tracking for all model activities  