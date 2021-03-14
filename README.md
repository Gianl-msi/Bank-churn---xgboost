# Background - Problem Statement
For the credit card companies acquiring new customers is a lengthly and costly process. Thus, customer's attrition is one the utmost interest of financial firms. To reduce attrition rate, one immediate solution is to engage those clients who are projected to churn with enticing offers such as discounts, rebates or other perks.

# Tasks 
1 - The goal of this project is to train a ML classifier that can help the financial firms to single out who will churn in the future. Since churning is a rare event and but it has significant financial repercussion, the model should focus on reducing the recall rate. Predict non-churning customers as churned won't harm the business, but predicting churning customers as non-churning will do and should be avoided.   
2 - Once the model is perfected, the most important features that lead the clients to leave business will be isolated. These features will help the finacial firm to identify which clients to target.

# EDA 
The dataset is available on kaggle (https://www.kaggle.com/sakshigoyal7/credit-card-customers). It consists of 10127 customers and 18 features and one column for the class (current customer, churned customer). 

<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/pie2.png" width="300" height="300"/>

The figure above the distribution of
As expected the number of churned customers is significantly smaller than the number of those who didn't churn.

<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/age.png" width="300" height="300"/>
<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/contacts.png" width="300" height="300"/>
<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/credit_limit.png" width="300" height="300"/>
<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/gender.png" width="300" height="300"/>
<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/dependent.png" width="300" height="300"/>
<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/marital%20status.png" width="300" height="300"/>

# Modeling

<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/summary.png" width="300" height="300"/>
<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/summary_x_test.png" width="300" height="300"/>
<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/force_plot%20negative.png" width="300" height="300"/>
<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/force_plot%20positive.png" width="300" height="300"/>
<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/missclas-1.png" width="300" height="300"/>
<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/missclas-2.png" width="300" height="300"/>
