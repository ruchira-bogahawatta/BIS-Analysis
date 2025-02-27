# BIS Assignment
# Finance - Credit Risk Assessment

## Overview
This project focuses on analyzing a dataset to identify key factors influencing loan defaults and develop a predictive model for credit risk assessment. The process includes data preprocessing, exploratory data analysis(EDA), statistical modeling, and visualization to uncover patterns and insights. The goal is to extract meaningful insights and build models for prediction and help financial institutions make informed lending decisions and mitigate risks.

## Dataset

- **Source:** Kaggle (https://www.kaggle.com/datasets/laotse/credit-risk-dataset/data)
- The dataset includes simulated credit bureau data with 32,581 records with 12 features.
- **Features**
  
| Feature                     | Description                                                                 | Data Type  |
|-----------------------------|-----------------------------------------------------------------------------|-----------|
| **person_age**              | Age of the individual applying for the loan.                               | Integer   |
| **person_income**           | Annual income of the individual.                                           | Integer   |
| **person_home_ownership**   | Type of home ownership of the individual. <br> - **Rent**: The individual is currently renting a property. <br> - **Mortgage**: The individual has a mortgage on the property they own. <br> - **Own**: The individual owns their home outright. <br> - **Other**: Other categories of home ownership. | String    |
| **person_emp_length**       | Employment length of the individual in years.                             | Integer   |
| **loan_intent**             | The intent behind the loan application.                                   | String    |
| **loan_grade**              | The grade assigned to the loan based on creditworthiness. <br> - **A**: The borrower has a high creditworthiness, indicating low risk. <br> - **B**: The borrower is relatively low-risk, but not as creditworthy as Grade A. <br> - **C**: The borrower's creditworthiness is moderate. <br> - **D**: The borrower is considered to have a higher risk compared to previous grades. <br> - **E**: The borrower's creditworthiness is lower, indicating a higher risk. <br> - **F**: The borrower poses a significant credit risk. <br> - **G**: The borrower's creditworthiness is the lowest, signifying the highest risk. | String    |
| **loan_amnt**               | The loan amount requested by the individual.                              | Integer   |
| **loan_int_rate**           | The interest rate associated with the loan.                              | Float     |
| **loan_status**             | Loan status. <br> - **0 (Non-default)**: The borrower successfully repaid the loan as agreed. <br> - **1 (Default)**: The borrower failed to repay the loan according to the agreed-upon terms and defaulted. | Integer   |
| **loan_percent_income**     | The percentage of income represented by the loan amount.                 | Float     |
| **cb_person_default_on_file** | Historical default record of the individual. <br> - **Y**: The individual has a history of defaults on their credit file. <br> - **N**: The individual does not have any history of defaults. | String    |
| **cb_person_cred_hist_length** | The length of credit history for the individual.  


## Steps in the Analysis

1. **Data Cleaning & Preprocessing**
   - Identifying and handling NULL/Empty values - Imputation done using median
   - Identifying and handling Outliers - IQR is used to cap extreme values at appropriate thresholds
   - Encoding categorical variables using Label Encoding and One Hot Encoding
   - Removing duplicates

2. **Exploratory Data Analysis (EDA) & Visualization**
   - Summary statistics
   - Feature engineering - Performed Binning to create meaningful feature groups.
   - Visualizations:
      - 📊 **Boxplots & Bar Charts** to analyze distributions and category frequencies
      - 📊 **Heatmap** to examine correlations between numerical features
      - 📈 **Scatter Plots** for correlation analysis
   - Derived observations based on trends and relationships identified in the visualizations
     
3. **Predictive Analysis**
   - Feature Scaling perfomed using `StandardScaler()`
   - Utilized `Random Forest Classifier` to build the prediction model
   - Evaluated model performance using Classification Report and Precision-Recall Analysis
   - Feature importance was extracted and visualized using Random Forest

**Model Evaluation**

| Class | Precision | Recall | F1-Score | Support |
|-------|------------|--------|----------|---------|
| **Non-Default (0)** | 0.93 | 0.97 | 0.95 | 7351 |
| **Default (1)** | 0.86 | 0.75 | 0.80 | 2055 |
| **Accuracy** |  |  | **0.92** | 9406 |
| **Macro Avg** | 0.90 | 0.86 | 0.87 | 9406 |
| **Weighted Avg** | 0.92 | 0.92 | 0.92 | 9406 |

- Model indicates strong predictive capabilities for assessing credit risk given an applicant’s features (income, loan amount, employment length, etc.)
- This enables organizations to make data-driven decisions, optimize risk management, reduce loan defaults, and minimize financial losses


## Key Findings 

   - Most loan applicants are in the 20-25 and 26-35 age groups, with the 26-35 group being the largest. This suggests organizations should focus on younger individuals, as they are more likely to apply for loans.
   - Low-middle and middle-income groups have the most loan applications, but default rates are higher among low-income groups. Higher-income groups show lower defaults, highlighting that income plays a key role in predicting loan repayment and can help improve risk models.
   - The majority of applicants rent (50.9%) or have a mortgage (41.2%), which suggests the need for rental-based credit scoring models.
   - Loan defaults are higher among low-income individuals with smaller loans, while high-income individuals have fewer defaults. This indicates income is a strong predictor of repayment ability, and organizations should consider stricter criteria or additional checks for low-income applicants to improve risk assessment.
   - Low-income individuals are at a higher risk of default, even for smaller loans. This is evident from the concentration of defaults in the lower-left region of the scatter plot, where both income and loan amounts are low. In contrast, higher-income individuals (on the right side of the plot) show fewer defaults, even with larger loan amounts.
   - The loan grade, loan-to-income ratio, and loan interest rate are the strongest predictors of loan default. Borrowers with low loan grades, high loan-to-income ratios, and high interest rates are at a greater risk of default. This suggests that organizations should implement stricter credit evaluations for these borrowers to mitigate the risks.


## Future Improvement
   - The target variable has an imbalanced distribution, with fewer defaults than non-defaults. Consider using techniques like SMOTE or class weighting in the model to address this imbalance
   - Model performence can be furhter improved through techniques like Hyperparameter tunning and advanced feature engineering
