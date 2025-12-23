# Assignment 3 - Data Analytics (WS25)
### Mobile Price Classification Using CRISP-DM & PROV-O Documentation  
**Authors:** Muhammad Ibrar & Ahmad Ibrahim  


## Project Overview

This project applies the **CRISP-DM** methodology to classify mobile phones into four price ranges (0–3) based on their technical specifications.  
All analytical steps are accompanied by **PROV-O provenance tracking** and dataset documentation using **Schema.org** and **Croissant**.

Dataset used:  
**Mobile Price Classification** – https://www.kaggle.com/datasets/iabhishekofficial/mobile-price-classification

Completed CRISP-DM phases:

- **Phase 1 – Business Understanding**  
- **Phase 2 – Data Understanding**  
- **Phase 3 – Data Preparation**  
- **Phase 4 – Modeling**  
- **Phase 5 – Evaluation**  
- **Phase 6 – Deployment**  


## 1. Business Understanding (Completed)

This phase defines the project motivation and goals:

- **Scenario:** A new mobile company aims to understand how device features drive price range to support competitive pricing.
- **Business Objectives:** Predict the mobile phone price range class using device attributes to support pricing decisions and product positioning.
- **Business Success Criteria:** Usage by pricing/product teams, reduced time for initial pricing, and improved consistency of decisions.
- **Data Mining Goals:** Build a multi-class classifier for `price_range` (0–3) and provide probability outputs for uncertainty-aware decisions.
- **Data Mining Success Criteria:**  
  - Accuracy ≥ 90% on validation/test  
  - Macro F1 ≥ 0.88 and no class recall < 0.80  
  - Stable performance across splits  
  - Probabilities reasonably calibrated for decision use
- **AI Risk Considerations:** Misclassification risk, model drift, over-reliance without expert review, and potential subgroup performance differences.

All elements were logged using **PROV-O entities and associations**.


## 2. Data Understanding (Completed)

### Dataset structure documented using Schema.org & Croissant  
### Exploratory Data Analysis includes:

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
- RAM shows strong correlation with `price_range` (ρ ≈ 0.92).
- Some noise-like values exist but could reflect older device models.
- Outliers were found but not removed due to domain uncertainty.

All analyses were documented using **PROV-O Activities**.


## 3. Data Preparation (Completed)

### Quality checks performed:

- Duplicate detection  
- Missing value check  
- Outlier identification  
- Noise tagging  
- Data quality summary (with provenance)

### Preprocessing actions considered but not applied:

- No global scaling on the full dataset (scaling is performed inside the SVM pipeline to avoid leakage)
- No binning (not needed for balanced continuous data)
- No encoding (categorical features already numeric)
- No noise removal (values may represent valid older devices)
- No outlier removal (insufficient justification)
- No feature removal based solely on Pearson correlation

### Additional documentation:

- Potential derived attributes: screen area, pixel density, camera score, etc.  
- Potential external data sources: market prices, device catalogs, manufacturer specs

### Prepared Dataset:

Since no destructive preprocessing was applied, the modeling dataset is the same as the loaded dataset and is referenced consistently in provenance as `:data`.


## 4. Modeling (Completed)

- Train/validation/test split with stratification and reproducibility (fixed random seeds).
- SVM modeling using a pipeline that includes `StandardScaler` to avoid data leakage.
- Hyperparameter tuning performed using GridSearchCV (StratifiedKFold CV).
- All parameter settings tested and results were documented in the knowledge graph.
- Hyperparameter tuning process was supported by plots/figures and stored as report artifacts.


## 5. Evaluation (Completed)

- Final model evaluated on held-out test data with rich metrics (accuracy, macro/micro precision/recall/F1).
- Confusion matrix generated and saved as a figure.
- Baselines included majority-class and seeded random classifier for reference.
- External benchmark values were documented using the referenced Kaggle notebook.
- Performance was compared against Business Understanding success criteria.
- A technical bias audit was included using `four_g` as a subgroup attribute to check whether the model performs worse on “legacy” non-4G phones.


## 6. Deployment (Completed)

- Deployment recommendations provided with links to Business Objectives and Success Criteria.
- Ethical/risk considerations documented with links to AI risk aspects.
- Monitoring plan defined with triggers for intervention (drift, performance drop, subgroup gaps).
- Reproducibility reflection included (seeds, split strategy, pipeline design, logged provenance).


## Project Status

| CRISP-DM Phase | Status | Notes |
|---|---|---|
| **Business Understanding** | Completed | Fully documented with PROV-O |
| **Data Understanding** | Completed | Includes EDA, correlation, outlier/noise detection |
| **Data Preparation** | Completed | No destructive transformations required |
| **Modeling** | Completed | SVM + tuning + provenance |
| **Evaluation** | Completed | Test metrics + baselines + benchmark + bias audit |
| **Deployment** | Completed | Recommendations + monitoring + reproducibility reflection |


## Final Deliverables

- Provenance Knowledge Graph capturing all CRISP-DM phases
- Figures (tuning curve, confusion matrix, EDA plots)
- Auto-generated LaTeX report compiled from KG content
