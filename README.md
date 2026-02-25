# Hospital Readmission Risk Prediction (UCI Diabetes Dataset)

## Overview
This project analyzes hospital readmissions and builds machine learning models to predict whether a patient will be readmitted within **30 days** using demographic, clinical, and treatment-related features.

The goal is to support healthcare teams with earlier risk identification so they can improve discharge planning and post-hospital follow-up.

## Business Problem
Hospital readmissions within 30 days are a major healthcare challenge because they increase costs and can indicate gaps in care continuity. This project explores whether patient demographics and medical history can be used to predict 30-day readmission risk and compares predictive models for this task.

## Dataset
- **Source:** UCI Machine Learning Repository — Diabetes 130-US hospitals dataset
- **Size:** **101,766 observations**
- **Variables:** **50**
- **Target variable:** `readmitted` with values `NO`, `>30`, `<30`

### Target Definition Used for Modeling
For binary classification:
- **Positive class (1):** `<30` (readmitted within 30 days)
- **Negative class (0):** `NO` or `>30`

## Tools & Technologies
- **Python** (pandas, NumPy, scikit-learn)
- **Jupyter Notebook**
- **Power BI** (for related dashboarding workflows)
- **imbalanced-learn (SMOTE)**
- **Matplotlib / Seaborn** (visualization)

## Project Workflow
1. **Data Understanding & EDA**
   - Explored readmission distribution and demographic trends
   - Reviewed clinical and treatment-related variables

2. **Data Preprocessing**
   - Handled missing values (e.g., removed low-value high-missing columns like `weight` / `payer_code`)
   - Replaced missing categorical values with `"Unknown"` or `"None"` where appropriate
   - Encoded binary, ordinal, and multi-class features

3. **Imbalance Handling**
   - Applied **SMOTE after train/test split** to avoid data leakage
   - Balanced the training set for model training

4. **Modeling**
   - Logistic Regression (baseline, interpretable)
   - Random Forest Classifier

5. **Evaluation**
   - Compared models using accuracy, precision, recall, and F1-score
   - Interpreted model tradeoffs for healthcare use cases

## Key Results
### Logistic Regression
- **Accuracy:** 0.582
- **Recall (Positive Class):** 0.417
- **Precision (Positive Class):** 0.117
- **F1 (Positive Class):** 0.182

**Interpretation:** Better at catching readmitted patients (higher recall), but with many false positives.

### Random Forest
- **Accuracy:** 0.824
- **Recall (Positive Class):** 0.109
- **Precision (Positive Class):** 0.137
- **F1 (Positive Class):** 0.121

**Interpretation:** Higher overall accuracy, but misses many actual readmissions (low sensitivity).

## Feature Insights
The most influential predictors included:
- `change` (medication regimen changes)
- `metformin`
- `A1Cresult_>8`
- Admission type (urgent/emergency indicators)
- Demographic factors such as age and gender

These results suggest that treatment instability, metabolic control, and patient complexity are important signals for readmission risk.

## Business Takeaways
- A **recall-focused model** (like Logistic Regression in this project) may be more useful when the goal is to identify more at-risk patients for intervention.
- Findings support stronger **post-discharge follow-up** and care continuity, especially for clinically complex patients.
- This model can be used as a **screening tool** to flag patients for further review (not as a standalone clinical decision system).

## Repository Contents
- `analysis/analysis.ipynb` — full EDA, preprocessing, modeling, and evaluation workflow
- `report/Healthcare Analysis.pdf` — project report / writeup
- `images/` — figures used in this README (optional but recommended)

