# Banking-Regulations-Analysis

[Here](https://github.com/dborgesm/Banking-Analytics/blob/master/Banking_Regulation.ipynb) is the analysis and assessment of the capital requirement of our credit portfolio, all the definitions and calculations are based on [Basel Committee on Banking Supervision](https://www.bis.org/bcbs/irbriskweight.pdf) and Office of The Superintendent of Financial Institutions documentations ([OSFI](https://www.osfi-bsif.gc.ca/Eng/fi-if/rg-ro/gdn-ort/gl-ld/Pages/CAR19_chpt6.aspx)). The capital requirement calculated was for a bank which portfolio is composed by retail, mortgages and corporate exposures, the foundational and standard approach were used and the Basel III PDs and LGDs were applied.

# Advanced Internal Rating-Based Modelling

In this analysis is presented how to create a scorecard using [Lending Club](https://www.lendingclub.com) loan data, the steps involved are data preprocessing, normalizing the data using weight of evidence, modelling using logistic regression and measuring the performance of the model with the help of the confusion matrix and the ROC curve.
In addition, two Loss Given Default models were develop using Random Forest and XGBoosting, the importance of the features will be analyzed, and the final model will be selected comparing performance metrics.

## Data preprocessing
1. [Data preprocessing for a credit scoring application model](https://github.com/dborgesm/Banking-Analytics/blob/master/Data_Preprocessing_for_Credit_Scoring_Application.ipynb) 

2.  [Data preprocessing for a Loss Given Default (LGD) model](https://github.com/dborgesm/Banking-Analytics/blob/master/Data_Preprocessing_for_LGD_model.ipynb). The only difference from the process above is that here the objective variable was the LGD and the correlation between the LGD and the other variables was analyzed. 

The process of cleaning included spotting missing values, filtering irrelevant variables, detecting outliers and treating them, coarse classification and recoding categorical variables. It is important to mentioned that this is an unbalanced data there are approximately only 13% default cases.


