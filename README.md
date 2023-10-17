# Extended Length of Stays in Hospital: A Predictive Analysis Using Machine Learning

# Abstract 
This project aims to understand and predict the significant factors influencing extended length of stay in hospitals, defined as stays lasting seven days or more. Utilizing machine learning models, including Logistic Regression, Random Forest, and Random Forest, this study attempts to provide meaningful insights for healthcare professionals to optimize patient care. 
Keywords: Extended length of stay, machine learning, logistic regression, random forest, healthcare. 

# Introduction
Hospitalization duration significantly affects both patient well-being and healthcare system costs. Predicting extended hospital stays can assist in streamlining patient care, optimizing hospital resource utilization, and forecasting potential challenges. Extended length of stay in hospital is defined as stays in hospital lasting seven days or more. This project evaluates the length of stays in hospitals, identifies the impact of various patient parameters on their length of stay, and builds machine learning models that can effectively predict extended lengths of stay.

# Methodology 
## 2.1 Data Source and Preprocessing: 
We sourced our dataset from Microsoft's repository (https://github.com/microsoft/r-server-hospital-length-of-stay/tree/master/Data), which consists of 100,000 records and encompasses 28 distinct features, including both categorical and continuous variables. The continuous attributes, such as hematocrit, neutrophils, and sodium levels, were directly measured, while categorical features like gender and facility ID (‘facid’) were transformed into numerical values to facilitate model compatibility. Furthermore, all binary classification flags were encoded as categorical variables. Importantly, our meticulous data examination revealed the absence of any missing values or outliers within the dataset. 

