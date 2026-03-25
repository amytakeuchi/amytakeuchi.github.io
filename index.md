## Portfolio

---
## Geo Incrementality Measurement — Causal Inference Pipeline
Paid social campaigns are easy to run and hard to measure. Attribution tools overcount. Last-click models ignore cannibalization. Aggregate sales trends conflate campaign effects with seasonality. The only credible answer is a **geo experiment** with a **rigorous causal estimator** — but even then, a single model is not enough.

This project builds a **production-style geo incrementality measurement pipeline** across 60 markets, implementing **five causal estimators in parallel (DiD, TBR, CUPED, CUPAC, Synthetic Control, Bayesian Hierarchical)**, a **spillover-aware validity gate**, and a business reporting layer that translates statistical lift into **iROAS with full confidence interval propagation**.

The central finding is not the lift estimate — it is that **three of the five estimators fail** on the same dataset for different, diagnosable reasons: **DiD inverts the sign due to spillover contamination**, TBR attenuates by 16% for the same reason, and the **initial Synthetic Control overshoots ground truth by 18×** due to a donor scaling bug that passed **LOO stability checks**. Identifying, diagnosing, and fixing the SCM failure — collapsing pre-fit RMSPE from 51,332 to 1,998 — is the core technical contribution.

The three valid methods (CUPED, SCM, Bayes hierarchical) **converge on a consensus range** of 83K–94K incremental units against a **ground truth of 91.5K**. The primary estimator is selected by a **rule-based validity gate** that ranks on **CI availability**, not point accuracy — because an **iROAS without confidence bounds is not a reportable business metric**.

<a href="https://github.com/amytakeuchi/Spillover-Aware-Geo-Incrementality-Experiment-Pipeline/tree/main">View code on Github</a>
<br>
Debugging write-up: <a href="https://medium.com/@a.takeuchi121/building-a-production-grade-geo-incrementality-system-how-synthetic-control-failed-by-18-and-bd497ebefa08"> Building a Production-Grade Geo Incrementality System: How Synthetic Control Failed by 18× — and What Fixed It →
</a>

---
## Bayesian Marketing Mix Modeling — Geo-Experiment Calibration
Marketing attribution typically forces a choice between biased observational models and expensive experiments. For this project, I developed a production-grade Bayesian implementation to determine the optimal allocation of a $500K experimentation budget: should it be spent on more geo-tests or on improving model specification?

Working with 156 weeks of spend data, I engineered an end-to-end causal inference pipeline in PyMC 5.0. The system features a custom "fusion" layer that utilizes Bayesian precision weighting to automatically calibrate observational priors with experimental evidence. This ensures that the model only shifts its beliefs when experimental data is statistically more precise than historical trends, preventing over-correction from high-variance tests.

The core technical finding was that architectural rigor—specifically adding a trend component to capture organic growth—improved model $R^2$ by 58% (0.479 to 0.755) and reduced error by 30%. In contrast, the expensive geo-experiment calibration resulted in a 0% change in $R^2$. This "null" result provided a critical business insight: the observational model was already highly accurate, validating that the $500K budget was better spent on data quality than further testing.

The final model identified a 5–15% lift opportunity through budget reallocation from saturated TV channels to high-ROI Search and YouTube, providing a clear, risk-adjusted roadmap for spend optimization with full 94% HDI uncertainty propagation.

<a href="https://github.com/amytakeuchi/Bayesian-MMM-Calibrated-with-Incrementality/blob/main/README.md#bayesian-marketing-mix-model-with-geo-experiment-calibration">View code on Github</a>

---
## Causal Price Elasticity Estimation — Double Machine Learning Pipeline
 
Retailers and marketplace platforms lose revenue daily by pricing from intuition rather than causal evidence — because standard regression conflates correlation with causation (endogeneity). This project applies Double Machine Learning (DML) to the Kaggle Avocado Prices dataset (90,000+ weekly records, 54 U.S. markets) to recover causally valid own-price elasticity (PE) and promotional demand multiplier (TPRC) estimates for three avocado SKUs across Online and Offline channels.
 
I built the full two-stage DML pipeline from scratch: a cross-fitted nuisance stage (K-fold, time-ordered) that residualises price and demand on confounders X — including multi-harmonic Fourier seasonality, geographic entity fixed effects across 54 cities, and channel-specific price models — followed by a final OLS stage with HC3-robust standard errors and traffic-light reliability flags. A key debugging effort lifted nuisance model R² from 0.003 → 0.282 (94×) by identifying a silent double-removal of geographic signal rooted in the Frisch-Waugh-Lovell theorem, turning all six item × channel estimates from Yellow to Green.
 
<a href="https://github.com/amytakeuchi/Avocado-Price-Elasticity-DML">View code on Github</a>
<br>
Debugging write-up: <a href="https://medium.com/@a.takeuchi121/debugging-a-broken-causal-pipeline-how-a-frisch-waugh-lovell-insight-lifted-r%C2%B2-from-0-003-to-0-282-88a1559341bf">Debugging a Broken Causal Pipeline: How a Frisch-Waugh-Lovell Insight Lifted R² from 0.003 to 0.282 →</a>
 
---

## Mobile Game A/B Testing
Cookie Cats, a top-grossing mobile puzzle game, uses a monetisation 'gate' — a forced wait or in-app purchase — to generate revenue as players progress. A product team needed to decide whether placing this gate at Level 30 or Level 40 maximises Day-1 and Day-7 player retention, the metrics most directly linked to long-term lifetime value.

Working with 90,000+ player records, I designed the full hypothesis testing framework end-to-end: defined null and alternative hypotheses grounded in behavioural economics (the 'hedonic adaptation' mechanism behind gate placement), checked randomisation validity and sample-ratio mismatch, selected and applied a two-proportion z-test with Bonferroni correction for multiple comparisons, and quantified effect size via relative lift and bootstrap confidence intervals. Gate 30 produced a statistically significant +18.2% improvement in Day-7 retention (p < 0.01), with a 95% CI that excludes zero — providing a clear, actionable recommendation to the product team.

### [Project Summary Page](/ABTesting)

<a href="https://github.com/amytakeuchi/AB-Testing/tree/main">View code on Github</a>
<br><br>
 <img src="images/Cookiecat_cover.png?raw=true"/>

## Other Past Projects
---
### Customer Churn Classification
A leading telecommunications company was facing high customer attrition and needed a way to identify which users were most likely to cancel their service based on customer behavior, contract type, and service usage.

In this project, I (1) conducted exploratory data analysis (EDA) and created 20+ visualizations to uncover key patterns in customer churn behavior, (2) engineered domain-specific features from raw customer data, assessed multicollinearity, and applied SMOTE to address class imbalance, (3) developed and compared Logistic Regression, Random Forest, XGBoost, and AdaBoost models using GridSearchCV, improving Logistic Regression accuracy from 0.26 to 0.81 and F1 score by 50% from 0.42 to 0.63. All modeling and analysis were performed in Python using Scikit-learn, XGBoost, and Pandas.

<a href="https://github.com/amytakeuchi/Customer-Churn-Classification">View code on Github</a>

---
### Marketplace Listing Price Prediction
Mercari, a Japanese online marketplace, is confronting a challenge to determine the product listing price based on different product categories, brand names, and specs and make suggestions about the optimal selling price to the sellers.

In this project, I (1) created 20+ Visualizations to identify the patterns and trends for the pricing of listed products, (2) built a listing price recommendation tool based on listing features and different Linear Regression models, using Python ScikitLearn and Pandas, (3) conducted Topic Modeling to identify the top 10 topics that appear in the descriptions of listings and visualized using PCA and t-SNE; performed extensive text data cleaning.
<br><br>
<a href="https://github.com/amytakeuchi/Marketplace-price-prediction">View code on Github</a>

<img src="images/Mercari_img.png?" width="600" height="300"/>

[![](https://img.shields.io/badge/Python-white?logo=Python)](#) [![](https://img.shields.io/badge/Jupyter-white?logo=Jupyter)](#) [![](https://img.shields.io/badge/Google-white?logo=Google)](#) [![](https://img.shields.io/badge/sklearn-white?logo=scikit-learn)](#)[![](https://img.shields.io/badge/pandas-white?logo=pandas)](#)
 
---
### Healthcare Analytics
#### Diabetes Prediction
In this project, I created visualizations and built binary classification models using Logistic Regression, Random Forest, and Gradient boosting to predict diabetes using patient data. Involves data visualization and preprocessing in PCA and resampling using ADASYN.

<a href="https://github.com/amytakeuchi/Healthcare-Analytics/tree/main">View code on Github</a>

<img src="images/Diabetes_prediction.png?raw=true"/>



---
### Chicago Divvy bike share membership prediction
Divvy, a prominent bike share service offered in Chicago, offers annual membership while users have the option to use one-time payment as casual users. The provider is trying hard to convert casual users to subscribe to annual membership.

This project encompasses (1) extensive exploratory data analysis (EDA) on rideshare service data, employing statistical techniques and visualization tools to gain insights into user behavior and patterns.
(2) Developed a binary classification tool to predict the membership status of the users. Assessed 5 different Machine Learning models (Logistic Regression, KNN, Naive Bayes, Gradient Boosting, Random Forrest) and utilized the most effective model to enable targeted marketing for future strategic initiatives. Improved the training F1 score 33.3% by examining feature selection using Mutual Information.
(3) Retrieved, cleaned, and integrated Chicago's weather data using Python.

<a href="https://github.com/amytakeuchi/Bikeshare-Membership-Classification-analysis">View code on Github</a>

<img src="images/Bike_img.png?" width="700" height="400"/>

---
### Fintech Customer Segmentation and Clustering
ELo, the largest payment service in Brazil, has been partnering with merchants to offer promotions or discounts to cardholders. They are trying to understand the customer lifecycle to tailor their offers to individual purchase patterns.

Implemented customer cohort analysis, RFM segmentation, and K-means clustering methodology to understand purchasing patterns based on transaction history data with 1.9 million rows, enabling actionable insights for targeted marketing campaigns, personalized customer experiences, and identification of high-value customers.

<a href="https://github.com/amytakeuchi/Customer-Merchant-Cohort-and-Clustering">View code on Github</a>

<img src="images/Elo_Kmeans.png?" width="400" height="400"/>


---
### ETL project of invoice data
Extracted, cleaned, transformed, merged, and warehoused a dataset of retail inventory data.

<br><br>
<a href="https://github.com/amytakeuchi/ETL/tree/main">View code on Github</a>

