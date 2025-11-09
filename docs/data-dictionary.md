
# Loan Default Risk Analysis-Data Dictionary

## Dataset Overiew

- *Volume*: 2.55lakh+ loan application records
- *Source*: Anonymized loan portfolio dataset
- *Time Period*: Multipe-Year data from 2013 to 2018
- *Primary use case*: Predictive risk assessment and portfolio analysis

## Table: LoanApplications

|   Column Name        |Data Type|Description & Business Significance                                      
...............................................................................................................
LoanID	               | String  | Unique loan identifier; Serves as Primary key for tracking individual loans
Age	                   | Int64   | Applicant's age; Correlates with financial stability indicators
Income	               | Int64   | Applicant's Income; Debt-to-income ratio calculations
LoanAmount	           | Int64   | Approved Loan amount; Increases exposure
CreditScore	           | Int64   | Applicant's credit score; Key risk indicator
MonthsEmployed	       | Int64   | Number of months the applicant has been employed; Correlates with financial stability indicators
NumCreditLines	       | Int64   | Number of active credit lines per applicant; Indicates credit utilization behavior, higher numbers may signal financial stress or established credit history
InterestRate           | Double  | Annual interest rate assigned to the loan; Directly impacts borrower's repayment capacity and lender's profitability, risk-based pricing indicator	
LoanTerm	             | Int64   | Duration of the loan in months; Shorter terms typically mean higher monthly payments but lower total interest; affects default probability
DTIRatio	             | Double  | Debt-to-Income ratio (monthly debt payments ÷ monthly income); Critical risk indicator
Education	             | String  | Highest education level completed; Correlates with financial literacy and income potential 
EmploymentType	       | String  | Category of employment (e.g., Full-time, Part-time, Self-employed)
MaritalStatus	         | String  | Applicant's marital status; Indicates income stability
HasMortgage	           | Boolean | Indicates if applicant has an existing mortgage; Homeownership suggests financial stability and asset ownership
HasDependents	         | Boolean | Indicates if applicant has financial dependents; More dependents reduce disposable income
LoanPurpose	           | String  | Intended use of loan funds; Risk varies significantly by purpose (e.g., debt consolidation vs. home improvement)
HasCoSigner	           | Boolean | Indicates presence of a loan co-signer; Co-signers provide repayment guarantee substantially reduces default risk
Default	               | Boolean | Indicates if loan defaulted (1) or not (0); Target variable for risk modeling, key outcome for portfolio performance analysis
Loan Date (DD/MM/YYYY) | DateTime| Date when loan was originated; Enables time-based analysis of trends, seasonality, and economic impact on defaults


## Derived Fields
- **CreditScoreBins**: Categorical credit score ranges (very low: <400, low: <=450>, medium: <=650>, High: 650+)
- **Age Groups**: Life stage categories (Teen: <=19, Adult: <=39, Middle Aged: <=59>, Senior Citizen: 59+)
- **Income Bracket**: Categorical Income ranges (Low income: <30000, Medium income: >=30000 and <=60000, High: >=60000)


## Data Quality Notes
- Data provided in pre-cleaned state with no missing values
- The data types, column distribution, and data profile is still checked to ensure the data is free of inconsistencies. 
- Additional calculated columns are added using DAX to aid with the analysis. 

