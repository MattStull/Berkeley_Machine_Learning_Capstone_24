# Berkeley_Machine_Learning_Capstone_20.1

Jupyter Notebook Link

https://github.com/MattStull/Berkeley_Machine_Learning_Capstone_20.1/tree/main

Business Understanding

A financial metric that is popular in breaking down the return on equity (ROE) of a company is called the Dupont Analysis.  The Dupont Analysis breaks down the ROE into three components - profit margin X asset turnover X leverage.

I work for a financial institution in the corporate finance department.  Our company has a higher level of intangible assets to assets which limits our ability to enhance our ROE through leverage.  This results in the bank having to focus on profit margin and asset turnover to enhance ROE.  It should be noted there are other financial ratios that can be analyzed that feed into the 3 components of ROE I mentioned earlier.  

The questions I would like to answer are:

For companies that have a higher level of intangible assets to assets (similar to the bank I work for), how do other companies achieve above average ROE's through profit margin and asset turnover?
For those companies that generate high ROE's, what type of asset mix do they have that generates a high net interest margin that improves profit margin.
What is the deposit to branch ratio for companies that generate superior efficiency ratios that help improve profit margins.
What are salaries and benefits / asset ratios for companies that generate superior ROE's.
I plan to run DBScan to create classifications of banks based on similar characteristics and then run classification models on the data to answer the questions above.  A decision tree will be included as I plan to present this data to the executive management team of the financial institution I work for.

There may be other questions I will want to answer as I analyze the data.  This is actionable information I can present to our management team.

I have access to a 3rd party database (S&P Capital IQ) that contains hundreds of financial metrics for banks across the world. My focus will be banks located in the United States.  The number of banks that will be analyzed will be around 4,500.  The data in the analysis will be public information and there will be no confidentiality concerns.

https://www.capitaliq.spglobal.com
Links to an external site.

Answering this question is important as it will allow the bank to focus on ways to improve margin and efficiency.  It will also highlight the importance of executing acquisitions effectively and capturing the value that is modeled / paid for.

Data Understanding and Preparation

1.  The data was cleaned to remove text values from numeric fields and eliminated rows of data where the majority were NULL.
2.  Ran OneHotEncoding on the categorical features. I also ran PolynomialFeatures() with degree 2 but that did not help the accuracy.
3.  Added features that I thought would be helpful for the analysis and created a target feature for companies that generated a Return on Equity greater or equal to 12% in 2023.
4.  Removed columns that were not useful in the analysis.

Modeling

1.  Modeled a decision tree and logistic regression.
2.  Ran StandardScaler() on the data to help logistic regression run.
3.  Used a gridsearch to search for optimum parameters for each algorithm.

Results

Interestingly, the DecisionTree() performed poorly as compared to LogisticRegression().  The accuracy score was 67% for the decision tree and 90% for logistic regression.

Feature importances were also ran and it showed that Fiduciary Activities / Assets, Other Noninterest Exp / Assets, and Salary Expense / Assets were the strongest predictors of the outcome in Logistic Regression.

I did output the decision tree results graphically as well.

