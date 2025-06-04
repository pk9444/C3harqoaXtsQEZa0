# HAPPY CUSTOMERS

## CONTEXT

- The client is a fast growing startup firm in the logistics and delivery space, working with several partners and make on-demand delivery to their clients.
- They are facing various operational challenges and they are working towards addressing them and improving their business throughput.
- Now, they want to gauge how "Happy" or "Satisfied" their customers through a predictive mechanim, and take neccessary actions accordingly.
- For this, they have taken feedback from a customer cohort, based on 6 survey questions, compiled them in a dataset and provided a subset of it for the analytics.
- Based on the provided data description, there are some defined project goals that need to be achieved, and help the client scale up their business operations.

## DATA DESCRIPTION

- Y = target attribute (Y) with values indicating 0 (unhappy) and 1 (happy) customers
- X1 = my order was delivered on time
- X2 = contents of my order was as I expected
- X3 = I ordered everything I wanted to order
- X4 = I paid a good price for my order
- X5 = I am satisfied with my courier
- X6 = the app makes ordering easy for me

Attributes X1 to X6 indicate the responses for each question and have values from 1 to 5 where the smaller number indicates less and the higher number indicates more towards the answer.

## GOALS

- Using the provided, predict whether a given customer is Happy or not (1/0) based on different ratings, from 1 to 5, given by the customers as feedback.
- Achieve an accuracy of >= 73% in predicting customer happiness and determine the minimal set of relevant features that effectively contribute in predicting it. 
- Based on the predictive analysis performed, provide the neccessary business recommendations to the company that can help in improving customer satisfaction.

## METHODOLOGY

![Project_Lifecycle](https://github.com/user-attachments/assets/5265e233-bded-4dd2-972a-8fdec7723bf2)

## MACHINE LEARNING PIPELINE

![Model_Pipeline](https://github.com/user-attachments/assets/8a80397e-91e6-4181-b217-93a419cc5c63)

## CONCLUSION

### INSIGHTS FROM PERFORMANCE METRICS AND MODEL DEPLOYMENT
- The XGBoost model, tuned to the hyperparameters {'learning_rate': 0.1, 'max_depth': 3, 'n_estimators': 100, 'subsample': 1.0} is the best performing model with a 79.6% accuracy on the training set and 84.6% accuracy on the test set - well above the benchmark of expected 73% accuracy.
- The overall accuracy of the tuned XGBoost model when re-applied on the full dataset for validation turned out to be at 80.2%, indicating a strong generalization on the full dataset.
- The model exhibits a balanced performance across both target classes 0 and 1, with precision and recall both above 79% on the deployment set.
- Target Class '1' i.e. happy customers is predicted more reliably with a recall of 85.5% - useful for devising retention and loyalty strategies.
- Target Class '0' i.e. unhappy customers has a slightly lower recall of 73.7% - meaning some unhappy customers may go undetected.
- The model has a high F-1 measure of 77.1% and 82.5% for target class 0 and 1 respectively, indicating a solid balance between precision and recall.

  ### BUSINESS RECOMMENDATIONS
  
1. **Refine the survey by removing low-impact questions**
    - Based on the insights of the feature engineering and EDA, the questions X2: *" contents of my order was as I expected"* and X4: *"I paid a good price for my order"* have lower predictability. Hence, these can be safely removed to further streamline the survey.

2. **Retain and prioritize the high-impact survey questions**
    Following are the strongest predictive indicators of customer satisfaction:
    - X1 : *"my order was delivered on time"* - **Must Include**
    - X3: *"I ordered everything I wanted to order"* **Must Include**
    - X6 : *"the app makes ordering easy for me"* **Recommended to be included**
    - X5: *"I am satisfied with my courier"* **Recommended to be included**

3. **Leverage the high recall of XGBoost in predicting happy customer to build customer retention strategies**
- The XGBoost model has a recall of 85.5% in predicting happy customers (target class '1'), implying that it reliably detects who is satisfied based on questions X1, X3, X6 and X5.
- This insight can be used to find loyal customers segments and devise strategies to incentivize happy customers and retain them using loyatly programs, referral benefits, cashback etc. all with a lower risk of misclassification.

