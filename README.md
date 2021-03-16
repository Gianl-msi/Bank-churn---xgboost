# Background - Problem Statement
For the credit card companies acquiring new customers is a lengthly and costly process. Thus, customer's attrition is one the utmost interest of financial firms. To reduce attrition rate, one immediate solution is to engage those clients who are projected to churn with enticing offers such as discounts, rebates or other perks.

# Tasks 
1 - The goal of this project is to train a ML classifier that can help the financial firms to single out who will churn in the future. Since churning is a rare event and but it has significant financial repercussion, the model should focus on reducing the recall rate. Predict non-churning customers as churned won't harm the business, but predicting churning customers as non-churning will do and should be avoided.   
2 - Once the model is perfected, the most important features that lead the clients to leave business will be isolated. These features will help the finacial firm to identify which clients to target.

# EDA 
The dataset is available on kaggle (https://www.kaggle.com/sakshigoyal7/credit-card-customers). It consists of 10127 customers and 18 features and one column for the class (current customer, churned customer). 

<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/pie2.png" width="300" height="300"/>

The figure above shows that, as expected, the number of churned customers is significantly smaller than the number of those who didn't churn.

<p float="left">
  <img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/age.png" width="280" height="280"/>
  <img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/gender.png" width="280" height="280"/>
  <img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/dependent.png" width="280" height="280"/>
</p>
There is no a clear connection between the age, sex and number of dependents of the client and the orobability of churning.
Meanwhile, it seems clients who are married or signed up for more services are less prone to churn.   

<p float="left">
  <img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/marital%20status.png" width="280" height="280"/>
  <img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/Relationship.png" width="280" height="280"/>
</p>

The figure below shows all how the features are related to each other. 
- Age of the customer of the age is positivelly correlated to how long he/she has been a customer.
- The higher the number of transactions, the higher the total transaction amount
- The higher the balance, the higher the average utilization ratio.

<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/corr_png1.PNG" width="900" height="180"/>

# Modeling
## 1 - Vanilla Xgboost, NO GRID SEARCH 
The first xgeboost model trained utilized the default value for all the parameters. THe trained model generated 40 false negatives and 24 false positives.
Recall, F1 score and balance accuracy were 0.88, 0.90,0.93 respectively.
## 2 - Vanilla Xgboost, WITH GRID SEARCH 
Next we implemented gridsearch to find the best parameters, which were found to be:
gamma: 1, learning_rate: 0.4, max_depth: 4, reg_lambda: 0.25.
The tuned model generated 41 false negatives and 21 false positives. Recall, F1 score and balance accuracy were 0.87, 0.90, 0.93 respectively.
### Tuning of the positive class weight
Recall is the main metric we look at in this sort of problem. We could increase recall (thus dereasing FN) by increasing the scale_pos_weight parameters. However, we can let the number of false positive to explode, also. 
The ideal compromise sits where the total monetary loss of the firm is the minimun: this is equal to the sum of acquiring cost of the clients who left plus the cost of offers/deals/perks given away to maintain the clients. According to a marketing report of 2019, acquiring a new customer costs around 80 dollars. 
For the sake of this project we assume that the average cost of approaching a client with offers to discourage him/her from leaving the firm is 20 dollars per client. Thus, losing a customer is 4 times more expensive than enticing him/her to stay.

<p float="left">
  <img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/Recall%20F1.png" width="400" height="400"/>
  <img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/FN%20FP%20Cost.png" width="400" height="400"/>
</p>


<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/summary.png" width="400" height="400"/>
<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/summary_x_test.png" width="400" height="400"/>
<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/force_plot%20negative.png" width="800" height="100"/>
<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/force_plot%20positive.png" width="800" height="100"/>
The force plots below refer to two false negative predictions. 
<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/missclas-1.png" width="800" height="100"/>
<img src="https://github.com/Gianl-msi/Bank-churn---xgboost/blob/main/Figures/missclas-2.png" width="800" height="100"/>
