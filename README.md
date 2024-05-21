# Berkeley_Machine_Learning_Capstone_24

Jupyter Notebook Link

https://github.com/MattStull/Berkeley_Machine_Learning_Capstone_24/blob/main/Module%2024%20-%20Capstone%20Project.ipynb

Problem Statement

A financial metric that is popular in breaking down the return on equity (ROE) of a company is called the Dupont Analysis. The Dupont Analysis breaks down the ROE into three components - profit margin X asset turnover X leverage.

First Community Bank, a publicly traded company with the ticker FCBC, generated a return on equity of 11.23% in 2023. The average return on equity for all banks over time is approximately 12%.

The questions I would like to answer are:

1.  Which ratios of the Dupont Analysis were the greatest predictor of a company generating an ROE greater than 12%?
2.  What does the data suggest are areas of opportunity for improving profitability, specifically through efficiency?

A decision tree, logistic regression, and support vector classifier were ran to identify the best model for prediction. Decision trees were viewed as well to get an idea as to the characteristics of banks with higher profitability.

Answering this question is important as it will allow the bank to focus on ways to improve the profitability of the bank and help direct future strategy.

Data for Analysis

A 3rd party database (S&P Capital IQ) that contains hundreds of financial metrics for banks across the world is used to build the dataset. The dataset being used contains only banks located in the United States. The number of banks in the dataset is 4,549. The file name is 2023Y_Bank_Regulatory_Financials.xlsx

The data in the analysis is all public information and there are no confidentiality concerns.

https://www.capitaliq.spglobal.com
https://github.com/MattStull/Berkeley_Machine_Learning_Capstone_24/blob/main/2023Y_Bank_Regulatory_Financials.xlsx

Loading, Merging and Preprocessing Data¶
The excel file containing bank ratios contains 3 tabs of information that are then merged into a single dataframe. Once merged, the data distribution of each feature is analyzed. In addition, outliers are being excluded by removing any that have a z-score of 3.25 or greater. Rows and columns that contain a higher percentage of null values are excluded. Created additional features helpful for the prediction. Using a z-score of 3.25, the number of rows in the data file is reduced to 3,033. Rows with significant null values were removed. In addition, onehotencoding was ran on categorical features.

Modeling

Three models were ran:  decision tree, logistic regression and support vector classifier.  Logistic regression and svc performed the best.

Decision Tree

Although the performance of the decision tree had an accuracy of 64%, the tree was printed for viewing.  It did suggest 

https://github.com/MattStull/Berkeley_Machine_Learning_Capstone_24/blob/main/decision_tree.png

Logistic Regression Classification Report

Classification Report Metrics

Precision: This metric tells you what percentage of the predicted positive cases were actually positive.¶
Class 0 (ROE Less Than 12%): 0.92
This means that when the model predicted a sample to be in class 0, it was correct 92% of the time.

Class 1 (ROE Greater Than or Equal to 12%): 0.91
This means that when the model predicted a sample to be in class 1, it was correct 91% of the time.

Recall: This metric tells you what percentage of actual positive cases were correctly identified by the model.
Class 0 (ROE Less Than 12%):
This means that out of all actual class 0 samples, the model correctly identified 92% of them.

Class 1 (ROE Greater Than or Equal to 12%):
This means that out of all actual class 1 samples, the model correctly identified 91% of them

ROC AUC Score: 0.914
The ROC AUC (Receiver Operating Characteristic Area Under the Curve) score measures the ability of the model to distinguish between the two classes. A score of 0.914 indicates a high level of discrimination, meaning the model is very good at distinguishing between the positive and negative classes.

Features Importances

How to Interpret These Coefficients

Coefficient: Indicates the direction and strength of the feature's impact on the prediction. A positive coefficient means that as the feature value increases, the prediction also increases. Conversely, a negative coefficient means that as the feature value increases, the prediction decreases.

Absolute Coefficient: This represents the magnitude of the feature’s impact without considering the direction. It helps in understanding which features are most influential overall.

Importance in Decision-Making
Top Influencers: Features with the highest absolute coefficients (e.g., NII: Fiduciary Activities/ Avg Assets (%) and Other Noninterest Exp/ Avg Assets (%)) are the most critical for the model. These are the features that most significantly drive the predictions.

Moderate Influencers: Features with moderate absolute coefficients (e.g., Salary Expense/ Avg Assets (%), NII: Inv Bkg, Advsry, & Oth/ Avg Assets (%)) have noticeable but less dominant effects on the model’s output.

I was actually surprised by the results as initially hypothesized that the level of intangible assets a bank held would be a strong influencer, but the data proves otherwise.

Leveraging staff, managing other non-specific expenses, and increasing revenue from fiduciary activities that require little capital have the biggest impact on the overall predictability of return on equity.

Changing Feature Variables to Predict ROE Using Logistic Regression Predictor

The data shows that these 3 ratios have the highest influence in predicting the Return on Equity. Changing any one of these better by .17 will result in the predicted ROE of FCBC being greater than 12%.

Model Results Comparison
Based on the results, both Logistic Regression and the Support Vector Classifier are excellent choices, achieving nearly identical and high accuracy rates of 89%. The Decision Tree, while useful for understanding feature importance and interpretability, performed significantly worse with an accuracy of 64%.

Next Steps and Further Investigation
As mentioned earlier, feature importances showed Fiduciary Activities, Other Non-Interest Expense and Salaries (all 3 as a percentage of assets) having the strongest influence to predicting an ROE greater than 12%. Fiduciary Activity revenue is generated by expanding services such as Trust and Wealth Management Advisory. Other Non-Interest Expense is often-times by one-time items. Other ratios that are part of this analysis, however, can be used to identify areas causing salaries expense to assets to be higher. The logistic regression model predicts a .03 improvement in one of the 3 ratios above to generate an ROE of 12%.

As a result, two additional decision trees were ran to help determine other areas the bank should focus on to help improve ROE.

The first decision tree had a targeted (y-value) salaries to expense ratio of 1.50%, which is .03% better than FCBC's 1.53%. This decision tree had an accuracy of 72%. This tree predicts to generate a Salaries Expense / Asset ratio of 1.50% or better, Occupancy & Fixed Asset Expense / Assets needs to be better than .245%. FCBC's ratio is .34%. The tree also predicts if Occupancy & Fixed Asset Expense / Assets is higher than .245%, a Salaries Expense / Asset ratio of 1.50% or better can be achieved ultimately with average branch deposits greater than 39 million. First Community has an average branch deposit of 48 million. This would suggest the occupancy expense of the branch or average branch size increasing could help improve profitability.

https://github.com/MattStull/Berkeley_Machine_Learning_Capstone_24/blob/main/decision_tree_salariesexp.png

Further, an additional decision tree was ran on banks that generated Occupancy & Fixed Asset Expense / Asset ratios of .31% or better. FCBC's ratio is .34%. This was the target for the decision tree. The accuracy score of this decision tree was 77%. This tree predominantly predicted Fixed Asset to Asset ratios needed to be less than 1.53% to achieve the target Occupancy & Fixed Asset Expense / Asset ratio of .31% or better. The Fixed Asset to Asset ratio for FCBC is 1.56%. A branch of banks, however, did achieve a Fixed Asset Expense / Asset ratio of .31% or better if Fixed Assets / Assets were higher than 1.53%. This was achieved generally by having an Assets / FTE (full time equivalent employee) ratio of 6 million or greater. FCBC's Assets / FTE ratio of 5.2 million.

https://github.com/MattStull/Berkeley_Machine_Learning_Capstone_24/blob/main/decision_tree_occ_exp.png

Given the average branch deposits in a range that is acceptable, this would suggest non-earning assets or corporate employee levels are at inefficient levels and focus should be on these areas to improve profitability.