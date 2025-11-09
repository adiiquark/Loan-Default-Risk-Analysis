
# DAX Measures used in respective Dashboard pages
The Dashboard pages are:
- Overview and Loan Default Page
- Applicant Demographics and Financial Profile
- Financial Risk metrics

## Overview and Loan Default Page

-**Average Income by Employment Type**
Average Income by Employment type = 
CALCULATE(AVERAGE('Loan_default'[Income]),ALLEXCEPT(Loan_default,Loan_default[EmploymentType]))

-**Average Loan by Age group**
Average Loan by Age group = 
AVERAGEX(VALUES('Loan_default'[Age groups]),AVERAGE('Loan_default'[LoanAmount]))

-**Default rate by employment type**
Default rate by employment type = 
var totalrecords = COUNTROWS(ALL ('Loan_default'))
var DefaultCases = COUNTROWS(FILTER('Loan_default','Loan_default'[Default]=TRUE()))

RETURN 
CALCULATE(DIVIDE(DefaultCases,totalrecords),ALLEXCEPT('Loan_default','Loan_default'[EmploymentType]))*100

-**Default rate by year**
Default rate by year = 
 var total_loans = 
                CALCULATE(COUNTROWS('Loan_default'),
                ALLEXCEPT('Loan_default',Loan_default[Year]))

Var default = CALCULATE(COUNTROWS(FILTER('Loan_default',
                'Loan_default'[Default] = TRUE())), ALLEXCEPT('Loan_default',Loan_default[Year]))

RETURN
DIVIDE(default,total_loans)*100

-**Loan amount by purpose**
Loan amount by purpose = 
SUMX(FILTER('Loan_default', NOT(ISBLANK(Loan_default[LoanAmount]))),Loan_default[LoanAmount])


## Applicant Demographics and Financial Profile

-**Average Loan amount(High credit)**
Average_Loan_amount(High credit) = 
AVERAGEX(FILTER(Loan_default,Loan_default[Credit Score bins] =  "high"),
Loan_default[LoanAmount])

-**Loans by Education Type**
Loans by education type = 
COUNTROWS(FILTER(Loan_default,NOT(ISBLANK('Loan_default'[LoanID]))))

-**Median by Credit score bins**
Median by Credit Score bins = 
MEDIANX(Loan_default,Loan_default[LoanAmount])

-**Total Loan (Middle age adults)**
Total Loan (Middle Age adults) = 
SUMX(FILTER('Loan_default',Loan_default[Age groups]="Middle Aged"), Loan_default[LoanAmount])

-**Total Loan(Credit bins)**
Total Loan(Credit bins) = 
CALCULATE(SUM(Loan_default[LoanAmount]),
Loan_default[Age groups]="Adult", ALLEXCEPT(Loan_default, Loan_default[Age],
Loan_default[Age groups],Loan_default[CreditScore],Loan_default[Credit Score bins]))

## Financial Risk and metrics

-**YOY Default Loans Change**
YOY Default Loans Change = 
DIVIDE(
    CALCULATE(COUNTROWS(FILTER('Loan_default',
              'Loan_default'[Default]=TRUE())), 'Loan_default'[Year] = YEAR(MAX('Loan_default'[Loan_Date_DD_MM_YYYY]))) 
              -
              CALCULATE(COUNTROWS(FILTER('Loan_default',
              'Loan_default'[Default]=TRUE())), 'Loan_default'[Year] = YEAR(MAX('Loan_default'[Loan_Date_DD_MM_YYYY]))-1)

              ,CALCULATE(COUNTROWS(FILTER('Loan_default',
              'Loan_default'[Default]=TRUE())), 'Loan_default'[Year] = YEAR(MAX('Loan_default'[Loan_Date_DD_MM_YYYY]))-1),0) *100


-**YOY Loan amount change**
YOY Loan amount change = 
DIVIDE(
    CALCULATE(SUM(Loan_default[LoanAmount]),'Loan_default'[Year]=YEAR(MAX(Loan_default[Loan_Date_DD_MM_YYYY]))) -
    CALCULATE(SUM(Loan_default[LoanAmount]), 'Loan_default'[Year]=YEAR(MAX('Loan_default'[Loan_Date_DD_MM_YYYY]))-1)
     ,
     CALCULATE(SUM(Loan_default[LoanAmount]),'Loan_default'[Year]=YEAR(MAX('Loan_default'[Loan_Date_DD_MM_YYYY]))-1),0) *100


-**YTD Loan Amount**
YTD Loan Amount = 
CALCULATE(SUM('Loan_default'[LoanAmount]),DATESYTD('Loan_default'[Loan_Date_DD_MM_YYYY].[Date]),
ALLEXCEPT('Loan_default','Loan_default'[Credit Score bins],'Loan_default'[MaritalStatus]))
