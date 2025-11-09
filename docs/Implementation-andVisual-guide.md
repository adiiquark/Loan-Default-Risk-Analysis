
# Loan Default Risk Analysis - Implementation and Visual guide

## Data Architecture
### Data Pipeline
1. **Data Ingestion**:
- Source data loaded in to Microsoft using SSMS
- Established as a persistent data store for analysis

2. **Cloud Storage**:
- Created Power BI Dataflows to maintain a cloud copy of the dataset
- Enabled efficent data refresh and scalability

3. **Data Modeling**:
- Minimal Cleaning required (data provided in analysis-ready state)
- Standardized categorical variables for consistent reporting
- Created bins for credit scores and age groups for demograhic analysis

#### Measure Organization
- **Measure Table 1**: Overview and Loan Default metrics
- **Measure Table 2**: Applicant Demographics & Financial Profile metrics
- **Measure Table 3**: Time Analysis metrics

#### Performance Optimization
- Implemented incremental refresh for large dataset (250K+ rows)
- Optimized DAX measures with variables (VAR) for improved performance
- Used CALCULATE with appropriate filter contexts for accurate calculations

#### Deployment
- Published report to Power BI Service
- Configured incremental refresh settings for efficient data updates
- Set up scheduled refresh to maintain data currency

## Dashboard Architecture
### Page 1: Overview and Loan DefaultKey Visualizations:
- Loan amount by purpose (Line Chart)
- Average income by employment type (Line Chart)
- Default rate by employment type
- Default % by year (Line Chart)
- Average loan amount by age group (Line Chart)

**Business Questions Addressed**:
- Which loan purposes have the highest amounts?
- How does income vary across employment types?
- How does rate vary across employment types? 
- What are the default rate trends over time?
- How does loan amount vary by applicant age?

### Page 2: Applicant Demographics & Financial Profile
**Key Visualizations**:
- Median loan amount by credit score category (Line Chart)
- Total loans (adults) by credit score bins (Line Chart)
- Number of loans by education type (Bar Chart)

- Loans (middle aged adults) by mortgage/dependents (Stacked Column Chart)
- Average loan amount (high credit) by age groups and marital status (Donut Chart)

**Business Questions Addressed**:
- How does credit score affect loan amounts?
- What is the distribution of loans across credit score categories?
- How does education level correlate with loan applications?
- How do homeownership and dependents affect loans for middle-aged applicants?
- What are the loan characteristics of high-credit applicants across demographics?

### Page 3: Financial Risk Metrics
**Key Visualizations**:
- YOY default loans change (Line Chart)
- YOY loan amount change (Line Chart)
- YTD loan amount (Ribbon Chart)
- Decomposition tree for loan amount analysis by employment type and income bracket

**Business Questions Addressed**:
- How are default rates changing year-over-year?
- What are the trends in loan amounts over time?
- What is the year-to-date loan volume?
- What factors contribute most to total loan amount?

## Technical Considerations
### Data Volume Handling
- Optimized for large datasets (2.5Lakh+ rows)
- Implemented incremental refresh to minimize processing time
- Used appropriate aggregations to improve performance

### Security and Compliance
- No sensitive data included in shared artifacts
- Template approach maintains data confidentiality
- Followed data governance best practices

### Scalability
- Architecture supports additional data sources
- Measures designed for extensibility
- Refresh configuration accommodates growing data volumes
