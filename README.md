# mental-health-analysis
# 🌍 The Mentalists — Global Mental Health & Modeling

This repository analyzes **global mental health** patterns (prevalence, burden, treatment gaps) and builds **predictive models** using multiple disorders as features. It also includes a **Universal Health Coverage (UHC)** analysis with a **Sweden vs. United States** case study.

> Course: AAI 500 • Team project originally under the `AAI500TeamProject` org  
> This repo highlights my individual contributions.

---

## 📌 Objectives
- **Global lens:** Explore cross-country prevalence, disease burden (DALYs), symptom distributions, and treatment gaps.
- **Modeling lens:** Train and evaluate regression models (GLM, KNN, Random Forest, SVR; plus bivariate OLS fits) to predict disorder rates.
- **Equity lens:** Quantify the relationship between **UHC** and **depression** and compare **Sweden vs. US**.

---

## 🗂️ Data (loaded programmatically)
- Mental health CSVs (1990–2019): prevalence, DALYs, treatment coverage, symptoms.  
- UHC Index (long format by country–year).  
- Datasets are fetched via a GitHub API helper inside the notebook.

---

## 🔬 Methods & What’s in the Notebook

### 1) Data Engineering & Cleaning
- GitHub API loader pulls all CSVs for mental health indicators.
- Standardizes headers, trims whitespace, converts types, checks NAs.
- Keeps **outliers** to preserve real-world extremes important for policy.

### 2) Exploratory Data Analysis (EDA)
- **Boxplots/KDE** for distributions & outliers.
- **Histograms** per metric.
- **Scatter + pair plots** to inspect relationships.

### 3) Correlation, Covariance & Bivariate Regressions
- Heatmaps for **comorbidity patterns** across disorders.
- Example fits:
  - `anxiety_disorders → eating_disorders`
  - `bipolar_disorder ↔ eating_disorders`
  - `bipolar_disorder ↔ anxiety_disorders`
  - `schizophrenia_disorders → eating_disorders`
- Reports **R²** and **MSE** alongside visual regression lines.

### 4) Supervised Modeling (multifeature → single target)
Using Dataset #1 (prevalence), with features:
`[schizophrenia_disorders, depression_disorders, anxiety_disorders, bipolar_disorders]`
to predict **`eating_disorders`** (scaled + train/test split):
- **GLM (Gaussian)**
- **K-Nearest Neighbors Regressor**
- **Random Forest Regressor**
- **Support Vector Regressor (RBF)**
- Unified `evaluate_model(...)` reports R²/MSE on train/test.

> Note: The notebook’s full ML pipeline is centered on **predicting eating_disorders** from other disorders.  
> Bipolar is analyzed extensively in **bivariate regressions** (relationships with anxiety/eating), not as the multivariate target.

### 5) Universal Health Coverage (UHC) Analysis
- **Merge** UHC Index (country–year) with mental health data.
- **Averages by country**: UHC vs. average **depression** rate.
- **Year-by-year** scatter + correlation (2000–2019).
- **Hypothesis test**: Pearson correlation (UHC vs. depression) with CI; negative association.
- **OLS regression**: UHC → depression (β < 0), model summary in notebook.

#### Case Study: **Sweden vs. United States**
- Visual comparison highlights **higher UHC** in Sweden and **lower average depression** vs. the US.
- Shows how coverage can align with improved mental-health outcomes, while noting socio-economic and system-design caveats.

---

## 🔎 Key Findings
- **Comorbidity patterns:** Strong links among several disorders (e.g., anxiety–eating, bipolar–dysthymia); multicollinearity in some indicators.
- **Modeling:** Predicting **eating disorders** from other disorders yields meaningful R² in several fits; bivariate regressions show clear positive slopes for pairs like anxiety→eating and bipolar↔eating.
- **Treatment gaps:** Anxiety treatment coverage inversely tracks untreated rates; large untreated shares persist in some regions.
- **UHC & depression:** Negative association overall; regression supports that **higher coverage ↔ lower depression rates** (population-level signal).
- **Sweden vs. US:** Sweden’s higher UHC pairs with lower average depression compared to the US, illustrating equity implications.

---

## 🙋 My Contributions (what I did)
- **Global framing & equity:** Positioned the work as a **global mental health** study (prevalence, DALYs, treatment, UHC), not just code.
- **Data pipeline:** Wrote the GitHub API ingestion + cleaning for **7+ datasets**.
- **Statistical EDA:** Built correlation/covariance heatmaps, bivariate OLS fits with R²/MSE and plots.
- **Modeling:** Implemented and evaluated **GLM, KNN, Random Forest, SVR** to predict **eating_disorders** from other disorders.
- **UHC analysis:** Merged UHC with mental-health metrics, ran **correlation tests**, **OLS**, and the **Sweden vs. US** case study; wrote interpretations.

---

## 📁 Repo Structure
