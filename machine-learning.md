[Go back to main page →](index.md)
# Machine Learning/Predictive Modeling

Predictive modeling and applied ML.

### Featured Projects
---
## Marketplace Listing Price Prediction

Built a two-part pricing intelligence system on 148K+ marketplace listings: a regression-based price recommendation engine using listing features (category, brand, condition, shipping) and an NLP pipeline using LDA topic modeling to surface the 10 dominant seller description clusters. t-SNE cluster analysis identified four high-signal, separable categories — deals/bundles, women's apparel, phones, and home goods — directly informing where category-specific pricing rules add the most business value. Findings revealed that 89%+ of listings contain fewer than 20 words, diagnosing a structural data quality gap with direct implications for seller tooling and model confidence.

<br><br>
<a href="https://github.com/amytakeuchi/Marketplace-price-prediction">View code on Github</a>

<img src="images/Mercari_img.png?" width="600" height="300"/>

[![](https://img.shields.io/badge/Python-white?logo=Python)](#) [![](https://img.shields.io/badge/Jupyter-white?logo=Jupyter)](#) [![](https://img.shields.io/badge/Google-white?logo=Google)](#) [![](https://img.shields.io/badge/sklearn-white?logo=scikit-learn)](#)[![](https://img.shields.io/badge/pandas-white?logo=pandas)](#)
 
---
## Customer Churn Classification
A leading telecommunications company was facing high customer attrition and needed a way to identify which users were most likely to cancel their service based on customer behavior, contract type, and service usage.

In this project, I (1) conducted exploratory data analysis (EDA) and created 20+ visualizations to uncover key patterns in customer churn behavior, (2) engineered domain-specific features from raw customer data, assessed multicollinearity, and applied SMOTE to address class imbalance, (3) developed and compared Logistic Regression, Random Forest, XGBoost, and AdaBoost models using GridSearchCV, improving Logistic Regression accuracy from 0.26 to 0.81 and F1 score by 50% from 0.42 to 0.63. All modeling and analysis were performed in Python using Scikit-learn, XGBoost, and Pandas.

<a href="https://github.com/amytakeuchi/Customer-Churn-Classification">View code on Github</a>

---
## Healthcare Analytics
#### Diabetes Prediction
In this project, I created visualizations and built binary classification models using Logistic Regression, Random Forest, and Gradient boosting to predict diabetes using patient data. Involves data visualization and preprocessing in PCA and resampling using ADASYN.

<a href="https://github.com/amytakeuchi/Healthcare-Analytics/tree/main">View code on Github</a>

<img src="images/Diabetes_prediction.png?raw=true"/>

---
## Chicago Divvy bike share membership prediction
Divvy, a prominent bike share service offered in Chicago, offers annual membership while users have the option to use one-time payment as casual users. The provider is trying hard to convert casual users to subscribe to annual membership.

This project encompasses (1) extensive exploratory data analysis (EDA) on rideshare service data, employing statistical techniques and visualization tools to gain insights into user behavior and patterns.
(2) Developed a binary classification tool to predict the membership status of the users. Assessed 5 different Machine Learning models (Logistic Regression, KNN, Naive Bayes, Gradient Boosting, Random Forrest) and utilized the most effective model to enable targeted marketing for future strategic initiatives. Improved the training F1 score 33.3% by examining feature selection using Mutual Information.
(3) Retrieved, cleaned, and integrated Chicago's weather data using Python.

<a href="https://github.com/amytakeuchi/Bikeshare-Membership-Classification-analysis">View code on Github</a>

<img src="images/Bike_img.png?" width="700" height="400"/>
