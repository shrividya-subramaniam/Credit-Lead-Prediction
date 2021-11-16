# Credit-Lead-Prediction
 Solution to Analytics Vidhya Job-a-thon 2 Hackathon Problem
 
## Problem Statement
Happy Customer Bank is a mid-sized private bank that deals in all kinds of banking products, like Savings accounts, Current accounts, investment products, credit products, among other offerings.The bank also cross-sells products to its existing customers and to do so they use different kinds of communication like tele-calling, e-mails, recommendations on net banking, mobile banking, etc.In this case, the Happy Customer Bank wants to cross sell its credit cards to its existing customers. The bank has identified a set of customers that are eligible for taking these credit cards.

Now, the bank is looking for your help in identifying customers that could show higher intent towards a recommended credit card, given: customer details (gender, age, region etc.), details of his/her relationship with the bank (Channel_Code,Vintage, 'Avg_Asset_Value etc.).

**Data Dictionary**

Variable | Definition
--- | ---
ID | Unique Identifier for a row
Gender | Gender of the Customer
Age | Age of the Customer (in Years)
Region_Code | Code of the Region for the customer
Occupation | Occupation Type for the customer
Channel_Code | Acquisition Channel Code for the Customer  (Encoded)
Vintage | Vintage for the Customer (In Months)
Credit_Product | If the Customer has any active credit product (Home loan, Personal loan, Credit Card etc.)
Avg_Account_Balance | Average Account Balance for the Customer in last 12 Months
Is_Active | If the Customer is Active in last 3 Months
Is_Lead(Target) | If the Customer is interested for the Credit Card  (0 : Customer is not interested, 1 : Customer is interested)

## Evaluation Metric
ROC AUC Score is used to evaluate model performance of the classifiers. 

## Approach
The bank requires us to predict probability of interested customers opting for a credit card. Hence, this is a classification problem. 

The proportion of classes in the target variable is imbalanced. Stratified K-Cross validation technique is used to ensure both classes of the dependent variable are equally represented during building the models and model evaluation. 

The data has higher number of observations compared to the number of features. Therefore, low bias high variance machine learning models like K-NN, tree based models are ideal for this problem to prevent underfitting. The ensemble models: XGBoost, CatBoost and LightGBM perform well acheiving a ROC AUC score of ~0.86. The average of the predicted values from these models are considered as the final predicted values.
