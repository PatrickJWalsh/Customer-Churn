# Customer-Churn


### Source and Project Code 
This dataset is modified from the one stored at the UCI data repository (namely, the area code and phone number have been deleted). This is artificial data similar to what is found in actual customer profiles.  The data can be downloaded [here].

### Project Introduction and Motivation
Classification problems are one of the main use cases for machine learning.  Specifically, customer churn is an issue that threatens all subscription-based companies (the loss of customers).  Detection of customers that will likely churn will result in substantial savings, as the cost of retention is often far lower than the cost of acquiring new customers.  The dataset consists of 5000 customers of a telecom company.  My goals are to better understand the customer base (through exploratory data analysis), to determine the strongest predictors of churn, and to identify cost-savings to the company by creating a model to predict customer churn.

### Methods Used
All analysis was performed in R. Select tables and model outputs were formatted in Excel. 

* Exploratory Data Analysis and Descriptive Statistics
* Data Visualization
* Supervised Machine Learning (Logistic Regression and Random Forest Classification)

## Project Highlights
* Created logistic regression model and random forest model to classify customer churn, resulting in the identification of 62% cost savings for a telecom company based on  retention and customer acquisition costs
* Utilized a deviance table and variable importance test to determine that total day charge, number of service calls, and international plans are the strongest predictors
of customer churn for the telecom company
* Conducted exploratory data analysis to understand the customer base and to develop actionable recommendations such as manipulating pricing strategy and service offering


Cost Savings Image on Balanced Data
Variable importance Plot
ROC Curve

## Procedure


### Data Cleaning and Exploratory Data Analysis
Some manipulation was performed on this data. The *accountlength* variable was originally listed in days, so I binned this into intervals of 3 months to exist as a factor.
After that, the original *accountlength* feature was removed from the data. 

![image](https://user-images.githubusercontent.com/71853253/95395132-e0eddb80-08cb-11eb-8537-a1c9f6ee824f.png)

Within each time of the day, as well as with international service, there were multiple features (*minutes, calls, total charged*), and as visible in the correlation plot, minutes and amount charged had a 1-1 correlation.  There is no need for redundant variables, and intuitively, the amount charged is the most relevant feature in terms of understanding churn, so *minutes and call* features were eliminated from the data. Otherwise, no strong correlations existed between the variables, meaning these variables are largely independent. 

Now, I wanted to understand the distribution of some features within the data.

![image](https://user-images.githubusercontent.com/71853253/95395842-8786ac00-08cd-11eb-898f-e124cdf2632c.png)

Only 9% of the customer base has an international plan.  Standalone, this figure seems quite low, so benchmarking this against competitors would be useful.  If this figure is indeed lower than expected, price manipulation and/or bundling services may entice more consumers to adopt this plan.  


![image](https://user-images.githubusercontent.com/71853253/95396728-848cbb00-08cf-11eb-9658-48935e303c07.png)

Only 26% of customers have a voicemail plan.  Similar to before, it would be interesting to know how this figure compares to competitors, and similar tactics can be used to employed to make this service more desirable for consumers.

![image](https://user-images.githubusercontent.com/71853253/95397904-68d6e400-08d2-11eb-8cc2-1156adcf1cda.png)

20% of customers have called 3 or more times. Only 20% of customers have not made a service call, and considering these plans have all been owned for under a year, the majority of customers run into some issue soon after starting their plan.  The company can look into simplifying certain services, and can consider alternative methods of troubleshooting (online/automated options).  It would be interesting to see if customers who have made more calls are more likely to churn, and I expect that to be the case.

Now that we understand the distribution of some of these variables, we should look at how churn is related to each.

![image](https://user-images.githubusercontent.com/71853253/95398584-2ca48300-08d4-11eb-9ec0-b1ad8fe83850.png)

There are a lower proportion of people with voicemail plans who churn than those without a voicemail plan who churn (7.71% and 16.45%, respectively).  Broadly speaking, consumers are happy with the voicemail plan offering, as those who own it are less likely to leave the company.  

![image](https://user-images.githubusercontent.com/71853253/95398988-22cf4f80-08d5-11eb-9bb1-4ffc6b7c1605.png)

42.07% of international plan users churned, whereas only 11.22% of non-international plan users churned, a staggering difference.  A few possible explanations may exist.  Consumers may realize soon after beginning the international plan that they are not getting enough value from the service.  Alternatively, these customers could be short-term travelers that are no longer in need of the service.  It is important to understand why these customers are dropping the service such that the company can respond accordingly.

![image](https://user-images.githubusercontent.com/71853253/95400299-52338b80-08d8-11eb-9124-0b7d3782fad7.png)

There was no clear relationship between churn and account length (period of time in which someone has owned the plan).  Churn rates for each bucket were between 12 and 15%.

![image](https://user-images.githubusercontent.com/71853253/95400457-a3dc1600-08d8-11eb-8452-24b264e5c611.png)

As expected, as the number of service calls a customer makes increases, so does the likelihood of them churning.  Consumers are likely increasingly frustrated with having to make multiple service calls, indicating that the customers service is lackluster, or that part of the service isn't intuitive enough for consumers to troubleshoot on their own.

### Training the Logistic Model

![image](https://user-images.githubusercontent.com/71853253/95401292-d850d180-08da-11eb-9aca-dab6a6ec6b19.png)

The model has a Mcfadden's R-squared value of .21, indicating it is a great fit. Unsurprisingly, *account length* was insignificant (as the earlier EDA suggested). 

![image](https://user-images.githubusercontent.com/71853253/95401659-cae81700-08db-11eb-8e3e-772576232ba6.png)

An analysis of the Deviance table indicates that *internationalplan* *totaldaycharge* and *numbercustomerservicecalls* are the most important variables in the model, as they have the largest effect on the deviance of the model.  The other features seem to contribute less to the model despite having low p-values in some cases.

### Predictions
Predictions were made on the test set, and the confusion matrix is as follows.

![image](https://user-images.githubusercontent.com/71853253/95402807-9cb80680-08de-11eb-925c-4cd1752fb426.png)

Recall = 18%
Precision = 53%
Accuracy = 86%

*How can recall and precision be so low and the overall accuracy so high*? The answer is that the data is imbalanced, as there are far more customers who don't churn than those who do.  We will revisit this problem later, but it was worth calling out for now.

![image](https://user-images.githubusercontent.com/71853253/95403139-63cc6180-08df-11eb-9d44-2a75a01aee35.png)

This plot shows that the majority of the predictions are skewed heavily towards 0 (as the majority of the data are customers who will not churn).  Due to the structure of the data, we should reconsider the classification threshold (originally set at .5) in hopes of correctly classifying more true positives (customers who churn).

![image](https://user-images.githubusercontent.com/71853253/95403373-143a6580-08e0-11eb-8e37-0afc6a273ea6.png)

This plot displays the classification accuracy by the threshold (previously .5).  It is clear that any value over .2 will produce a relatively similar accuracy. Again, this is possible due to the dominance of one class (non-churn).  Total accuracy is not the most important metric within the context of this problem, though.  We are trying to minimize the costs associated with maintaing the company's customer base, including the retention cost (money spent on existing customers) and the acquisition cost (money spent to acquire new customers to replace churned customers).  Knowing that customer acquisition cost is much more expensive than retention cost, we are looking to prioritize true positives (correctly identifying customers who would churn), and to reduce false negatives (incorrectly labeling a customer as someone who wouldn't churn, when in reality, they end up leaving the company).  I have created the following formula to display this relationship.

 *Cost_Model <- ((sum(TP) + sum(FP)) * Retention_Cost) + (sum(FN) * Acquisition_Cost)*

 *Retention_Cost <- 60*
 *Acquisition_Cost <- 300*

 *((39 + 34) * (60))  + (173 *300) = 56,200*

Upon classifying a customer as someone who would churn (whether they end up doing so or not, *TP + FP*), they will be incentivized to stay with the company through the retention cost.  In cases where the model incorrectly classified customers as not churning (false negative), these customers are being lost, and need to be replaced (with the customer acquistion cost).  If the company were to follow the predictions of the current model (before tuning), they would have to spend $56,200 to maintain their customer base.

CAC found [here](https://www.patriotsoftware.com/blog/accounting/what-is-customer-acquisition-cost/#:~:text=Customer%20acquisition%20cost%20by%20industry&text=Travel%20industry%3A%20%247%20per%20customer,Financial%20industry%3A%20%24175%20per%20customer)
Retention assumption drawn from [here](https://www.outboundengine.com/blog/customer-retention-marketing-vs-customer-acquisition-marketing/#:~:text=Acquiring%20a%20new%20customer%20can,customer%20is%205%2D20%25).

![image](https://user-images.githubusercontent.com/71853253/95404365-cecb6780-08e2-11eb-8d52-33fa2cea15af.png)

An AUC of .84 is high, and indicates that the model is generally a strong classifier.  The curve also displays the true poisitive rate and false positive rate, and the colored scales indicate these rates by classification threshold.  Choosing an appropriate classification threshold will largely depend on the costs associated with classification (tp, fp, tn, fn).  I will select a threshold of .17, as that seems to be near the point of diminishing returns (where an increase in true positive rate is accompanied by drastically more false positives). 














