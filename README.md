# vlGWTfBzYwNrtBs8

## Background:

We are a small startup focusing mainly on providing machine learning solutions in the European banking market. We work on a variety of problems including fraud detection, sentiment classification and customer intention prediction and classification.

We are interested in developing a robust machine learning system that leverages information coming from call center data.

Ultimately, we are looking for ways to improve the success rate for calls made to customers for any product that our clients offer. Towards this goal we are working on designing an ever evolving machine learning product that offers high success outcomes while offering interpretability for our clients to make informed decisions.

## Data Description:

The data comes from direct marketing efforts of a European banking institution. The marketing campaign involves making a phone call to a customer, often multiple times to ensure a product subscription, in this case a term deposit. Term deposits are usually short-term deposits with maturities ranging from one month to a few years. The customer must understand when buying a term deposit that they can withdraw their funds only after the term ends. All customer information that might reveal personal information is removed due to privacy concerns.

## Attributes:

    * age : age of customer (numeric)
    * job : type of job (categorical)
    * marital : marital status (categorical)
    * education (categorical)
    * default: has credit in default? (binary)
    * balance: average yearly balance, in euros (numeric)
    * housing: has a housing loan? (binary)
    * loan: has personal loan? (binary)
    * contact: contact communication type (categorical)
    * day: last contact day of the month (numeric)
    * month: last contact month of year (categorical)
    * duration: last contact duration, in seconds (numeric)
    * campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)

## Output (desired target):
    * y - has the client subscribed to a term deposit? (binary)

## Goal(s):

Predict if the customer will subscribe (yes/no) to a term deposit (variable y)
Success Metric(s):

Hit %81 or above accuracy by evaluating with 5-fold cross validation and reporting the average performance score.

## Bonus(es):

We are also interested in finding customers who are more likely to buy the investment product. Determine the segment(s) of customers our client should prioritize.
What makes the customers buy? Tell us which feature we should be focusing more on.

#### Method and Results
- **Exploratory data analysis**
   - I first explored the data to gain insights with the help of histograms of distributions of features and feature importance. Data exploration showed there was no missing data. The primary problem with the    dataset was presence of imbalance in dataset. The data seen was highly imbalanced as the minority class(yes) is representing less than 10% of the total samples. Hence, employed sampling alogorithms SMOTE which addressed the imbalance by generating synthetic samples for the minority class. It creates new instances by interpolating between existing minority class samples, making the dataset more balanced.

- ** Building models **
   - I then built several models: XGBoost, Random Forest, Decision Tree, Logistic Regression, Support Vector. I trained these models using training data (randomly selected from the whole dataset) at an 80% split. I compared these models along accuracy and F1 scores and elected to focus on LR models based on these results. Random Forest and XGBoost both seem pretty good so going ahead with testing them with the KFold Cross Validation.

- ** Improving the model **
   - Random Forest and XG Boost as both seem to have pretty good scores or Precision, Recall and F1-Score which are more important when dataset is imbalanced in Binary Classification problems. When the distribution is severely skewed, it is likely that one or more folds will have few or no examples from the minority class. This means that some or perhaps many of the model evaluations will be misleading, as the model need only predict the majority class correctly. Thus used the Stratified KFold Cross Validation method.

#### Conclusion
Success Metric Achieved: 5-fold stratified cross validation with **97.72%** recall:
I solved this binary classification problem with highly imbalanced dataset with Random Forest. And the success metric that was choosen recall with 97.72%. The reason for selecting recall as our main performance metric is that in this case, False Negatives are more important than False Positives. Let us say we are calling the customers for a new term insurance from our model results. Rather than calling everyone, we will only call customers who are more likely to buy. We cannot afford to miss a person who was going to buy the term insurance, but our model predicted it as Not buying(False Negative).

## Bonus questions solution

For this, **Agglomerative clustering algorithm** was used for customer segment selection which helped in finding the proper segment of customers most likely to buy the term insurance.
