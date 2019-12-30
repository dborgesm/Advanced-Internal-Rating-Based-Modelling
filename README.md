# Banking-Regulations-Analysis

[Here](https://github.com/dborgesm/Banking-Analytics/blob/master/Banking_Regulation.ipynb) is the analysis and assessment of the capital requirement of our credit portfolio, all the definitions and calculations are based on [Basel Committee on Banking Supervision](https://www.bis.org/bcbs/irbriskweight.pdf) and Office of The Superintendent of Financial Institutions documentations ([OSFI](https://www.osfi-bsif.gc.ca/Eng/fi-if/rg-ro/gdn-ort/gl-ld/Pages/CAR19_chpt6.aspx)). The capital requirement calculated was for a bank which portfolio is composed by retail, mortgages and corporate exposures, the foundational and standard approach were used and the Basel III PDs and LGDs were applied.

# Advanced Internal Rating-Based Modelling

In this analysis is presented how to create a scorecard using [Lending Club](https://www.lendingclub.com) loan data, the steps involved are data preprocessing, normalizing the data using weight of evidence, modelling using logistic regression and measuring the performance of the model with the help of the confusion matrix and the ROC curve.
In addition, two Loss Given Default models were develop using Random Forest and XGBoosting, the importance of the features will be analyzed, and the final model will be selected comparing performance metrics.

## Data preprocessing
1. [Data preprocessing for a credit scoring application model](https://github.com/dborgesm/Banking-Analytics/blob/master/Data_Preprocessing_for_Credit_Scoring_Application.ipynb) 

2.  [Data preprocessing for a Loss Given Default (LGD) model](https://github.com/dborgesm/Banking-Analytics/blob/master/Data_Preprocessing_for_LGD_model.ipynb). The only difference from the process above is that here the objective variable was the LGD and the correlation between the LGD and the other variables was analyzed. 

The process of cleaning included spotting missing values, filtering irrelevant variables, detecting outliers and treating them, coarse classification and recoding categorical variables. It is important to mentioned that this is an unbalanced data there are approximately only 13% default cases.

## Objective Variable

### Probability of Default Model 

In this case, the column loan status helped us to construct the objective variable, indeterminates were considered as people late more than 30 days. 

After the data preprocessing from 148 variables, 43 were left to model the PD. The variables that are going to help us to calculate the PD are the ones that contain information at the time of applying for a loan. For instance, annual income, employment length, debt to income, inquiries in the last 6 and 12 months, address region, residential status, maximum balance in revolving accounts, number of personal financial inquiries, between others.

### LGD Model 

The variables used to calculate the workout LGD are total payment, principal, interest, collection recovery fee, loan amount and principal paid, according to the following formula.

Workout LGD = 1-RR = 1 - (Recoveries/Exposure at Default)

WLGD = 1 - (Total Payment - Principal - Interest - Collection Recovery Fee) / (Loan Amount - Principal Paid)

After cleaning the data 45, variables were left, almost all the variables to model the PD were used to model the LGD; these variables contain information after the client has defaulted. For instance, the number of accounts open, delinquency history, maximum balance in the credit cards, and so forth. 

## Score Card Construction

First, the data was divided into training and testing (70%/30%), the indeterminates cases were removed only from the training sample. Then, the variables were binned using sequentially trees with the following constraints, 5% of minimum cases per final bins and a maximum of 50 bins, the cuts chosen, maximize the information value (IV), and gave an explainable trend. After this process and analyzing the IV, most variables had an information value less than 0.1 and not even close to 0.09, being to strict in this part will only left 3 variables for training so all the variables with less than 0.07 IV were removed, and LASSO is going to be used as a next filter. The code with all this process is [here](https://github.com/dborgesm/Banking-Analytics/blob/master/Normalizing_the_data_using_WOE.ipynb).

