# Extended Length of Stays in Hospital: A Predictive Analysis Using Machine Learning

# Abstract 
This project aims to understand and predict the significant factors influencing extended length of stay in hospitals, defined as stays lasting seven days or more. Utilizing machine learning models, including Logistic Regression, Random Forest, and Random Forest, this study attempts to provide meaningful insights for healthcare professionals to optimize patient care. 
Keywords: Extended length of stay, machine learning, logistic regression, random forest, healthcare. 

# 1) Introduction
Hospitalization duration significantly affects both patient well-being and healthcare system costs. Predicting extended hospital stays can assist in streamlining patient care, optimizing hospital resource utilization, and forecasting potential challenges. Extended length of stay in hospital is defined as stays in hospital lasting seven days or more. This project evaluates the length of stays in hospitals, identifies the impact of various patient parameters on their length of stay, and builds machine learning models that can effectively predict extended lengths of stay.

# 2) Methodology 
## 2.1) Data Source and Preprocessing: 
We sourced our dataset from Microsoft's repository (https://github.com/microsoft/r-server-hospital-length-of-stay/tree/master/Data), which consists of 100,000 records and encompasses 28 distinct features, including both categorical and continuous variables. The continuous attributes, such as hematocrit, neutrophils, and sodium levels, were directly measured, while categorical features like gender and facility ID (‘facid’) were transformed into numerical values to facilitate model compatibility. Furthermore, all binary classification flags were encoded as categorical variables. Importantly, our meticulous data examination revealed the absence of any missing values or outliers within the dataset. 

## 2.2) Feature Engineering: 
Date features (‘vdate’ and ‘discharged’) were converted from date [object] format to numeric[int]. 
We transformed the 'lengthofstay' variable, originally a continuous variable with a range from a minimum of 1 day to a maximum of 17 days, into a new categorical binary variable named 'ExtendedLOS,' where a value of 1 indicates a 'lengthofstay' of 7 days or longer and 0 denoted stays of less than 7 days. 
The 'gender' variable, originally coded as 'M' and 'F,' was transformed into a binary numeric format by creating a new variable called 'gender_M,' where 'M' is represented as 1 and 'F' as 0. 
The categorical variables 'facid,' which originally had values [A, B, C, D, E], and 'rcount,' initially coded as [1, 2, 3, 4, 5+], were both converted into a numeric representation. This transformation was achieved using the pd.get_dummies function, resulting in expanded columns with binary indicators for each category, effectively making them suitable for analysis and modeling purposes. 
Further, we assumed the differences between ‘vdate’ and ‘discharged’ are used to calculate the ‘lengthofstay’. For this reason, we dropped them out of the final data set. 

## 2.3) Data Splitting:
A holdout validation( train-validation-test) strategy was employed, partitioning the final dataset into an 80% training and 20% testing set. The dataset was divided into three subsets: a training set for model development, a validation set for hyperparameter tuning and model selection, and a test set held aside for the final evaluation of the trained model's performance on new, unseen data. 

## 2.4) Model Selection and Building: 
In our dataset, we have seen some levels of skewness. Hence, we implemented preprocessing techniques, including the use of the Standard Scaler for continuous variables and the OneHot Encoder for categorical variables. These strategies aim to standardize and encode the data appropriately, enhancing its suitability for subsequent modeling and analysis. Due to observed class imbalances in our target variable ('ExtendedLOS'), we proposed the use of a Random Forest model as a potential machine learning solution. We have employed both the Standard Random Forest and the Balanced Random Forest (BRF) algorithms. Additionally, we applied the SMOTE algorithm to enhance the robustness of our machine-learning model, addressing the challenges posed by the imbalanced dataset. 

# 3) Results
We were able to produce Table 1 using the TableOne package in Python. 

## 3.1) Logistic Regression Machine Learning Model: 
An initial accuracy of 92.14% was achieved on the validation dataset with precision (0.94), recall (0.68), and f1-score (0.74) for predicting extended stays. Post hyperparameter tuning, the model's performance exhibited a slight enhancement, a validation accuracy of 92.31%, and a slight decrease in precision (0.86), recall (0.62), and f1-score (0.72) for predicting extended stays. The tuned logistic regression model successfully predicts extended hospital stays with a balanced trade-off between precision and recall. 

## 3.2) Random Forest Machine Learning Model: 
We tried to explore both the Standard Random Forest and the Balanced Random Forest (BRF) model. Further, adjustments for class imbalance using class weight and SMOTE were attempted.

A. Standard Random Forest model: 
The model exhibited a remarkable training accuracy of 99.99% and a validation accuracy of 95.19% with precision (0.93), recall (0.74), and f1-score (0.83) for predicting extended stays (Class 1). 
With class imbalance adjustments using class_weight=’balanced’, the model shows a negligible dip in validation accuracy to 94.73% with precision (0.94), recall (0.72), and f1-score (0.81) for predicting extended stays (Class 1). Despite the high accuracy and precision, there was a modest decrease in recall after class weight compensation. Further, a Random Forest Classifier with SMOTE (Synthetic minority over_sampling technique) was employed to address class imbalance. With this approach, the model achieved an overall accuracy of 94.73%, with precision of 0.87, recall of 0.79, and F1-score of 0.83. 

B. Balanced Random Forest Model:
This model achieved an overall accuracy of 92% with a high recall of 0.94 for predicting Extended LOS(class 1). While the precision for Class 1 was lower at 70%, it is a trade-off for achieving a better recall. 
Balanced Random Forest Classifier with SMOTE applied and with this method, the model achieved an overall accuracy of 94.6% with a Precision of 0.86, recall of 0.79, and F1-score of 0.83. 
Comparing all these results, either Balanced Random Forest Classifier with SMOTE or Random Forest Classifier with SMOTE machine learning models show promising results in identifying Extended LOS. 

## 3.3) Champion Model Performance on never seen Test Data: 
In the final test of our champion model, the Random Forest Classifier with SMOTE achieved an impressive accuracy of 94.8%, demonstrating its robustness in identifying extended hospital stays. With a precision of 0.86, recall of 0.80, and f1-score of 0.83, the model strikes a good balance between correctly predicting extended stays and minimizing false positives.

## 3.4) Feature Importance: 
The most crucial feature predicting extended hospital stays was a history of five or more readmissions within 180 days. This was followed by medical parameters such as hematocrit, BMI, and glucose levels. Both patient history and medical parameters emerged as vital indicators of extended hospital stays. 

# 4) Discussion 
The study's results underscore the significance of combining patient history with medical parameters when forecasting extended hospitalization. Factors such as readmission frequency, BMI, and glucose levels play pivotal roles in determining hospital stay durations. 

# 5) Conclusion 
Machine learning models can effectively identify patients at risk of extended hospital stays. Such predictive insights offer healthcare professionals actionable information, potentially reducing prolonged hospitalizations and enhancing patient care. 

# 6) Recommendations
Healthcare facilities should consider leveraging machine learning tools for patient management. By understanding the key variables affecting extended hospital stays, these establishments can develop targeted interventions to improve patient outcomes and operational efficiency. 

# 7) Limitations
This study is based on data from a single institution, which might limit its generalizability. Future studies should incorporate multi-institutional data for a more comprehensive understanding. 




