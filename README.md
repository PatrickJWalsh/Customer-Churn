# Customer-Churn

## Table of Contents
  - [Source and Project Code](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#source-and-project-code)
  - [Project Introduction and Motivation](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#project-introduction-and-motivation)
  - [Methods Used](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#methods-used)
  - [Project Highlights](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#project-highlights)
  - [Data Cleaning and Exploratory Data Analysis](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#data-cleaning-and-exploratory-data-analysis)
  - [Logistic Regression Model](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#logistic-regression-model)
	  - [Feature Analysis](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#feature-analysis)
	  - [Predictions](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#predictions)
	  - [Model Assessment and Tuning](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#model-assessment-and-tuning)
	  - [Tuned Model](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#tuned-model)
	  - [Cost Breakdown](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#cost-breakdown)
  - [Random Forest](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#cost-breakdown)
	  - [Predictions](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#predictions-1)
	  - [Tuning](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#tuning)
	  - [Tuned Model](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#tuned-model-1)
	  - [Feature Analysis](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#feature-analysis-1)
	  - [Cost Breakdown](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#cost-breakdown-1)
  - [Balancing the Data](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#balancing-the-data)
	  - [Logistic Regression](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#logistic-regression)
	    - [Feature Analysis](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#feature-analysis-2)
	    - [Predictions](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#predictions-3)
	    - [Model Assessment and Tuning](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#model-assessment-and-tuning-1)
	    - [Tuned Model](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#tuned-model-2)
	    - [Cost Breakdown](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#cost-breakdown-2)
    - [Random Forest](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#random-forest-1)
    	 - [Predictions](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#predictions-4)
	   - [Tuning](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#tuning-1)
	   - [Tuned Model](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#tuned-model-3)
	   - [Cost Breakdown](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#cost-breakdown-3)
	   - [Feature Analysis](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#feature-analysis-3)
  - [Conclusion](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#conclusion)
	  - [Additional Info and Improving the Analysis](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/README.md#additional-info-and-improving-the-analysis)
	  
### Source and Project Code 
This dataset is modified from one stored at the UCI data repository (area code and phone number have been deleted). This is artificial data similar to what is found in actual customer profiles.  The data can be downloaded [here](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/churn.csv).  Project code can be found [here](https://github.com/PatrickJWalsh/Customer-Churn/blob/main/Telecom%20Churn%20Analysis.R).

### Project Introduction and Motivation
Classification problems are one of the main use cases for machine learning.  Specifically, customer churn (the loss of customers) is an issue that threatens all subscription-based companies.  Detection of customers that will churn will result in substantial savings, as the cost of retention is often far lower than the cost of acquiring new customers.  The dataset consists of 5000 customers of a telecom company.  My goals were to better understand the customer base (through exploratory data analysis), to determine the strongest predictors of churn, and to identify cost-savings for the company by creating a model to predict churn.

### Methods Used
All analysis was performed in R. Select tables and model outputs were formatted in Excel. 

* Exploratory Data Analysis and Descriptive Statistics
* Data Visualization
* Supervised Machine Learning (Logistic Regression and Random Forest Classification)
* Balancing data (Oversampling and Undersampling)

## Project Highlights
* Created logistic regression model and random forest model to classify customer churn, resulting in the identification of 64% cost savings for a telecom company to maintain its customer base
* Utilized a deviance table and variable importance test to determine that total day charge, number of service calls, and international plans are the strongest predictors
of customer churn for the telecom company
* Conducted exploratory data analysis to understand the customer base and to develop actionable recommendations such as manipulating pricing strategy and service offering

![image](https://user-images.githubusercontent.com/71853253/95515078-0c83cb00-098b-11eb-819d-7b0b362d7e42.png)


![image](https://user-images.githubusercontent.com/71853253/95517105-5e7a2000-098e-11eb-94a6-76c4246301ad.png)

![image](https://user-images.githubusercontent.com/71853253/95511363-5cf82a00-0985-11eb-9530-faa5dba0dd0a.png)

### Data Cleaning and Exploratory Data Analysis
Some manipulation was performed on this data. The *accountlength* variable was originally listed in days, so I binned this into intervals of 3 months to exist as a factor.
After that, the original *accountlength* feature was removed from the data. 

![image](https://user-images.githubusercontent.com/71853253/95395132-e0eddb80-08cb-11eb-8537-a1c9f6ee824f.png)

Within each time of the day, as well as with *internationalplan*, there were multiple features (*minutes, calls, total charged*), and as visible in the correlation plot, *minutes* and *amount charged* had a 1:1 correlation.  There is no need for redundant variables, and intuitively, the *amount charged* is the most relevant feature in terms of understanding churn, so *minutes and call* features were eliminated from the data. Otherwise, no strong correlations existed between the variables, meaning these variables are largely independent. 

**Now, we should try to understand the distribution of some features within the data.**

![image](https://user-images.githubusercontent.com/71853253/95640292-14ff0300-0a6a-11eb-804e-8861cb822fc0.png)

Only 9% of the customer base has an international plan.  Standalone, this figure seems quite low, so benchmarking this against competitors would be useful.  If this figure is indeed lower than expected, price manipulation and/or bundling services may entice more consumers to adopt this plan.  


![image](https://user-images.githubusercontent.com/71853253/95396728-848cbb00-08cf-11eb-9658-48935e303c07.png)

Only 26% of customers have a voicemail plan.  Similar to before, it would be interesting to know how this figure compares to competitors, and similar tactics can be employed to make this service more desirable for consumers.

![image](https://user-images.githubusercontent.com/71853253/95397904-68d6e400-08d2-11eb-8cc2-1156adcf1cda.png)

Only 20% of customers have not made a service call, and 20% of customers have called 3 or more times.  Considering these plans have all been owned for under a year, the majority of customers run into some issue soon after starting their plan.  The company can look into simplifying certain services, and can consider alternative methods of troubleshooting (online/automated options).  It would be interesting to see if customers who have made more calls are more likely to churn, and I expect that to be the case.

**Now that we understand the distribution of some of these variables, we should look at how churn is related to each.**

![image](https://user-images.githubusercontent.com/71853253/95398584-2ca48300-08d4-11eb-9ec0-b1ad8fe83850.png)

There are a lower proportion of people with voicemail plans who churn than those without a voicemail plan who churn (7.71% and 16.45%, respectively).  Broadly speaking, consumers are happy with the voicemail plan offering, as those who own it are less likely to leave the company.  

![image](https://user-images.githubusercontent.com/71853253/95398988-22cf4f80-08d5-11eb-9bb1-4ffc6b7c1605.png)

42.07% of international plan users churned, whereas only 11.22% of non-international plan users churned, a staggering difference.  A few possible explanations may exist.  Consumers may realize soon after beginning the international plan that they are not getting enough value from the service.  Alternatively, these customers could be short-term travelers that are no longer in need of the service.  It is important to understand why these customers are dropping the service such that the company can respond accordingly.

![image](https://user-images.githubusercontent.com/71853253/95400299-52338b80-08d8-11eb-9124-0b7d3782fad7.png)

There was no clear relationship between churn and account length (period of time in which someone has owned the plan).  Churn rates for each bucket were between 12 and 15%.

![image](https://user-images.githubusercontent.com/71853253/95400457-a3dc1600-08d8-11eb-8452-24b264e5c611.png)
![image](https://user-images.githubusercontent.com/71853253/95536275-a57d0b00-09b8-11eb-8e28-9813465ffe3d.png)

As expected, as the number of service calls a customer makes increases, so does the likelihood of them churning.  Consumers are likely increasingly frustrated with having to make multiple service calls, indicating that the customers service is lackluster, or that part of the service isn't intuitive enough for consumers to troubleshoot on their own.

### Logistic Regression Model
A logistic regression model was run on the training data.

![image](https://user-images.githubusercontent.com/71853253/95401292-d850d180-08da-11eb-9aca-dab6a6ec6b19.png)

The model has a Mcfadden's R-squared value of .21, indicating it is a great fit. Unsurprisingly, *accountlength* was insignificant (as the earlier EDA suggested). 

### Feature Analysis

![image](https://user-images.githubusercontent.com/71853253/95401659-cae81700-08db-11eb-8e3e-772576232ba6.png)

An analysis of the deviance table indicates that *internationalplan*, *totaldaycharge*, and *numbercustomerservicecalls*, are the most important variables in the model, as they have the largest effect on the deviance of the model.  The other features seem to contribute less to the model despite having low p-values in some cases.

### Predictions
Predictions were made on the test set, and the confusion matrix is as follows.

![image](https://user-images.githubusercontent.com/71853253/95402807-9cb80680-08de-11eb-925c-4cd1752fb426.png)

* Recall = 18%
* Precision = 53%
* Accuracy = 86%

*How can recall and precision be so low and the overall accuracy so high*? The answer is that the data is imbalanced, as there are far more customers who don't churn than those who do.  We will revisit this problem later, but it is worth calling out for now.

![image](https://user-images.githubusercontent.com/71853253/95403139-63cc6180-08df-11eb-9d44-2a75a01aee35.png)

This plot shows that the majority of the predictions are skewed heavily towards 0 (as the majority of the data are customers who will not churn).  Due to the structure of the data, we should reconsider the classification threshold (originally set at .5) in hopes of correctly classifying more true positives (customers who churn).

### Model Assessment and Tuning

![image](https://user-images.githubusercontent.com/71853253/95403373-143a6580-08e0-11eb-8e37-0afc6a273ea6.png)

This plot displays the classification accuracy by the threshold (previously .5).  It is clear that any value over .2 will produce a relatively similar accuracy. Again, this is possible due to the dominance of one class (non-churn).  Total accuracy is not the most important metric within the context of this problem, though.  We are trying to minimize the costs associated with maintaing the company's customer base, including the retention cost (money spent on existing customers) and the acquisition cost (money spent to acquire new customers to replace churned customers).  Knowing that customer acquisition cost is much more expensive than retention cost, we are looking to prioritize true positives (correctly identifying customers who would churn), and to reduce false negatives (incorrectly labeling a customer as someone who wouldn't churn, when in reality, they end up leaving the company).  I have created the following formula to display this relationship.

 *Cost_Model <- ((sum(TP) + sum(FP)) * Retention_Cost) + (sum(FN) * Acquisition_Cost)*

 * _Retention_Cost <- 60_
 * _Acquisition_Cost <- 300_

 *((39 + 34) * (60))  + (173 *300) = 56,200*

Upon classifying a customer as someone who would churn (whether they end up doing so or not, *TP + FP*), they will be incentivized to stay with the company through the retention cost.  In cases where the model incorrectly classified customers as not churning (false negative), these customers are being lost, and need to be replaced (with the customer acquistion cost).  If the company were to follow the predictions of the current model (before tuning), they would have to spend $56,200 to maintain their customer base.

CAC found [here](https://www.patriotsoftware.com/blog/accounting/what-is-customer-acquisition-cost/#:~:text=Customer%20acquisition%20cost%20by%20industry&text=Travel%20industry%3A%20%247%20per%20customer,Financial%20industry%3A%20%24175%20per%20customer).
Retention assumption drawn from [here](https://www.outboundengine.com/blog/customer-retention-marketing-vs-customer-acquisition-marketing/#:~:text=Acquiring%20a%20new%20customer%20can,customer%20is%205%2D20%25).

![image](https://user-images.githubusercontent.com/71853253/95404365-cecb6780-08e2-11eb-8d52-33fa2cea15af.png)

An AUC of .84 is high, and indicates that the model is generally a strong classifier.  The curve also displays the true positive rate and false positive rate, and the colored scales indicate these rates by classification threshold.  Choosing an appropriate classification threshold will largely depend on the costs associated with classification (tp, fp, tn, fn), which will vary by situation (company/industry/problem).  I will select a threshold of .17, as that seems to be near the point of the onset of diminishing returns (where an increase in true positive rate is accompanied by drastically more false positives).

### Tuned Model
After changing the classification threshold to .17 (refer to ROC plot), the following results correspond to the predictions. 

![image](https://user-images.githubusercontent.com/71853253/95537026-8b442c80-09ba-11eb-8d50-f06d2891315b.png)

* Recall = 75%
* Precision = 38%
* Accuracy = 79%

Note that recall dramatically increased (previously 18%), while precision decreased (previously 53%), driving down overall accuracy slightly.  This is okay though, as a low true positive rate is driving the majority of costs in this problem, so increasing recall is ideal.  

*Tuned_Cost_Model <- ((sum(TP2) + sum(FP2)) * Retention_Cost) + (sum(FN2) * Acquisition_Cost)*

*((160 + 258) * 60) + (52 * 300) = 40,680*

The cost of maintaining the customer base has dropped by $15,600 (28%) after tuning the classification threshold.  There are 2 more business cases to discuss. The first is a situation in which the company uses no predictions.  The second is a situation in which the company can achieve a tpr of 100% and a fpr of 0% (the ideal model to optimize cost), which have been modeled through the following equations.

*CostofnoPrediction <- sum(dftest$churn == 1) * Acquisition_Cost*

*OptimizedCost <- sum(dftest$churn ==1) * Retention_Cost*

### Cost Breakdown

![image](https://user-images.githubusercontent.com/71853253/95484010-eeec3c80-095d-11eb-85f5-23b377709970.png)

This plot illustrates the cost of maintaining the customer base corresponding with each scenario. The company can achieve 36% ($22,920) cost savings when following the predictions of the tuned logistic regression model compared to a scenario in which they do not predict any churn. 

### Random Forest 

OOB Error = 6.71%

![image](https://user-images.githubusercontent.com/71853253/95492412-0aa91000-0969-11eb-8846-9ae3be32059b.png)

### Predictions 

![image](https://user-images.githubusercontent.com/71853253/95516095-b879e600-098c-11eb-8ae7-6878076d0be6.png)

* Recall = 63%
* Precision = 96%
* Accuracy = 94%

### Tuning 
We will test to see if the number of trees and number of variables tested at each split should change.

![image](https://user-images.githubusercontent.com/71853253/95492854-af2b5200-0969-11eb-8589-6beb3f2ed6ef.png)

The oob error seems to become fairly stable after 200 trees, so we will use this in our tuned model.

![image](https://user-images.githubusercontent.com/71853253/95493098-fd405580-0969-11eb-8ef5-3bb8f27bfcda.png)

The error is lowest when testing 3 variables at each split, so we will use this in the tuned model.

### Tuned Model

OOB Error = 5.8%

![image](https://user-images.githubusercontent.com/71853253/95493271-41cbf100-096a-11eb-9f41-709cb0c66447.png)

### Predictions

![image](https://user-images.githubusercontent.com/71853253/95516338-17d7f600-098d-11eb-9944-7dcbc20c6484.png)

* Recall = 70%
* Precision = 92%
* Accuracy = 95%

The tuned model has increased recall, and lower precision, causing a very slight increase in accuracy (which will have cost saving implications).

### Feature Analysis

![image](https://user-images.githubusercontent.com/71853253/95493826-05e55b80-096b-11eb-806d-4cf2210a5b89.png)

*Totaldaycharge* is the most important variable in terms of gini and accuracy decrease. The other variables are sequenced differently based on the measure (gini vs. accuracy), so we should interpret these cautiously.  Particularly, mean decrease in impurity importance metrics are biased when potential predictor variables vary in their scale of measurement, or their number of categories.  This may explain why *voicemailplan* and *internationalplan* are ranked low in importance, as they are binary variables, whereas *internationalplan* is ranked the third most important in terms of accuracy of predictions.  It is also known that importance metrics are biased when predictor variables are highly correlated, leading to suboptimal predictor variables being preferred.  Fortunately, the variables here have extremely low correlation.

To illustrate the potential bias of using Gini as the sole criteria in assessing importance, I added a continuous variable, *random*, and retrained the model.  In theory, we should see that this new variable has the least predictive power on churn, but we may see that its gini decrease is fairly high given it is a continuous variable (1-100), resulting in its perceived importance to be higher than the other binary variables.  

![image](https://user-images.githubusercontent.com/71853253/95494784-750f7f80-096c-11eb-8946-6647e0190831.png)

As expected, the *random* variable was ranked near the middle of the predictor variables in terms of Gini decrease, ahead of *voicemailplan*.  On the other hand, *random* ranks last in accuracy decrease, as it should, as it has no relationship with *churn*.  When viewing the two measures holistically, it seems that *totaldaycharge*, *numbercustomerservicecalls*, *totalevecharge*, and *internationalplan* are the most important predictor variables.  This assessment compares similarly with the importance of the variables in the logistic regression model.  Furthermore, we can say with confidence that *totaldaycharge*, *numbercustomerservicecalls*, and *internationalplan* are 3 of the top 4 most important variables across both models.  

### Cost Breakdown

![image](https://user-images.githubusercontent.com/71853253/95495620-ab99ca00-096d-11eb-8d2d-9829c1191fa2.png)

Following the predictions of the random forest, the company can save 55% ($34,740) in costs to maintain the customer base.

## Balancing the Data

As mentioned before, we are dealing with imbalanced data, as over 90% of the sample consists of customers who do not churn.  Machine learning algorithms tend to struggle with imbalanced data, as ML algorithms seek to minimize overall error, and the minority class contributes very little to this.  In classification, this results in a bias towards the majority class (refer to confusion matrix for random forest to confirm this, as the error varies drastically across the two classes).  Oversampling, undersampling, and synthetic data generation are all methods to combat this issue, and thankfully, R has packages to handle this.

I used the package [ROSE](https://cran.r-project.org/web/packages/ROSE/ROSE.pdf) to balance the data.  The distribution in the new training and test sets are as follows.

![image](https://user-images.githubusercontent.com/71853253/95506884-92e5e000-097e-11eb-98be-9bce85b77850.png)

### Logistic Regression 

![image](https://user-images.githubusercontent.com/71853253/95507174-0687ed00-097f-11eb-88e4-fe08cc4cc041.png)

McFadden's R-Squared increased to .24, meaning the model is a stronger fit (.21 before). 

### Feature Analysis

![image](https://user-images.githubusercontent.com/71853253/95507528-8ca43380-097f-11eb-8772-0f4ecb6ed5e5.png)

The same three variables (*internationalplan*, *totaldaycharge*, and *numbercustomerservicecalls*) have the largest impact on the residual deviance in the model, however, *numbercustomerservicecalls* now has the largest impact.  This could be possible due to the oversampling technique, however, we can conclude that these 3 variables are still the most important.

### Predictions

![image](https://user-images.githubusercontent.com/71853253/95508453-07218300-0981-11eb-8688-2fa0da04dec8.png)

* balanced_recall = 80%
* balanced_precision = 76%
* balanced_accuracy = 79%

This outperforms previous model on the imbalanced data (even after tuning).  Previous recall was 75%, and precision was 38%.

### Model Assessment and Tuning

![image](https://user-images.githubusercontent.com/71853253/95508977-d3932880-0981-11eb-97d6-453549c766b4.png)

Notice the distribution of predictions now.  This distribution looks quite different than the heavy skew towards 0 as seen before.  These predictions are in line with what would be expected with more balanced data.

![image](https://user-images.githubusercontent.com/71853253/95511025-e22f0f00-0984-11eb-8549-6922afa944fb.png)

Note the contrast between this graph and that of the imbalanced data.  With the imbalanced data, the accuracy leveled off after a threshold around .2, which is due to the imbalance.  This output shows that the range of acceptable thresholds for achieving a high accuracy is much narrower, as a threshold that is too low or too high will misclassify a substantial amount of the data.  

![image](https://user-images.githubusercontent.com/71853253/95511363-5cf82a00-0985-11eb-9530-faa5dba0dd0a.png)

AUC is .85, indicating a strong fit.  Just as we did before, we are going to tune the classification threshold (this time to .4) to attempt to minimize cost (by manipulating tpr and fpr).

### Tuned Model

![image](https://user-images.githubusercontent.com/71853253/95511932-1d7e0d80-0986-11eb-9f65-0bf160e2327e.png)

* Recall = 89%
* Precision = 71%
* Accuracy = 78%

Tuning has resulted in higher recall (88% instead of 80%), and lower precision (71% instead of 76%) which should lead to slightly lower costs for the company.

### Cost Breakdown

![image](https://user-images.githubusercontent.com/71853253/95512282-9d0bdc80-0986-11eb-852a-eeb90bdace39.png)

As expected, the tuned model led to additional $9,120 in savings when compared to the untuned logistic regression with balanced data. Following the predictions of the tuned model, the company would save 64% ($135,540) in costs when compared to making no predictions.

### Random Forest 

OOB Error = 2.17%

![image](https://user-images.githubusercontent.com/71853253/95513938-1efd0500-0989-11eb-947f-7f7f97fd1291.png)

### Predictions

![image](https://user-images.githubusercontent.com/71853253/95515820-38ec1700-098c-11eb-976a-de1876517097.png)

* Recall = 80%
* Precision = 92%
* Accuracy = 87%

Improvement has been made, as recall has increased from 70 to 80%.

### Tuning 

![image](https://user-images.githubusercontent.com/71853253/95514461-f6293f80-0989-11eb-8931-a7a8ec719860.png)

It seems that 6 variables is the appropriate number to test at each split, so we will use that in our tuned model.

### Tuned Model

OOB Error = 1.83%

![image](https://user-images.githubusercontent.com/71853253/95514647-47d1ca00-098a-11eb-8f13-b7f4ae2e2ccf.png)

### Predictions

![image](https://user-images.githubusercontent.com/71853253/95515661-ffb3a700-098b-11eb-83d5-52b92ee416c7.png)

* Recall = 80%
* Precision = 93%
* Accuracy = 88%

Tuning the model provided slight improvement in predictions (1% higher precision and accuracy).  There seems to be some overfitting on the training set after balancing the data.   

### Cost Breakdown

![image](https://user-images.githubusercontent.com/71853253/95515078-0c83cb00-098b-11eb-819d-7b0b362d7e42.png)

After balancing the data, the tuned logistic regression model and random forest performed comparatively (results will slightly vary depending on predictions and sample splits, but *set.seed(101)* will replicate the results shown above.  
### Feature Analysis

![image](https://user-images.githubusercontent.com/71853253/95517105-5e7a2000-098e-11eb-94a6-76c4246301ad.png)

When working with balanced data, gini and accuracy suggest that *totaldaycharge*, *numbercustomerservicecalls*, *internationalplan*, and *totalevecharge* are the most important predictors of customer churn in the random forest model, so we can confidently state their strength as predictors.

## Conclusion 
Customer churn is an issue that threatens all subscription-based companies.  Early detection of churn will result in substantial savings, as the cost of retention is often far lower than the cost of customer acquisition.  In this analysis, I ran both a logistic regression and a random forest model to predict customers who would churn for a telecom company.  Both models led to strong predictions, with the random forest leading to more cost savings on imbalanced data, whereas both models performed comparatively on balanced data.  As expected, after balancing the data, predictions on churned customers improved (as the class was more represented in the data).  There was slight variation in the importance of the variables between the regression and random forest, with the regression placing slightly more weight onto *voicemailplan* and slightly less on totalevecharge, whereas the random forest ranks totalevecharge 3rd, and ranks *voicemailplan* fairly low (random forest will prefer continuous variables over binary).  Both analyses concluded that *totaldaycharge*, *numberservicecalls*, and *internationalplan* were 3 of the top 4 most important variables.  If the telecom company were to follow the predictions of the tuned model model on balanced data, it can save 64% in customer acquisition and retention costs (prior to balancing the data, 55% savings were achievable).  Not only are there opportunities for substantial cost savings, these results highlight *totaldaycharge*, *numberservicecalls*, and *internationalplan* as main drivers in customer churn, so these are the areas the company should first consider changing to become more profitable.

### Additional Info and Improving the Analysis
To further improve the model's predictive power, and to move towards the *"optimized cost"* model, more feature engineering can be performed.  Additionally, feature selection and ensemble modeling will likely improve accuracy.     

































