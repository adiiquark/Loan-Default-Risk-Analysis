# Loan Default Risk Analysis Dashboard

## Project Overview
A comprehensive Power BI dashboard analyzing loan default risk across 250,000+ loan applications. This solution identifies key risk factors, demographic patterns, and temporal trends to enable data-driven lending decisions and portfolio optimization.

## Key Features
- **Risk Assessment**: Multi-dimensional analysis of default risk factors
- **Demographic Insights**: Detailed breakdown by applicant characteristics
- **Time Intelligence**: Year-over-year and year-to-date trend analysis
- **Advanced Visualizations**: Decomposition trees, ribbon charts, and interactive filtering
- **Enterprise Architecture**: Dataflows, incremental refresh, and cloud deployment

## Dashboard Pages
1. **Overview and Loan Default**: High-level metrics and risk indicators
2. **Applicant Demographics & Financial Profile**: Detailed demographic analysis
3. **Time Analysis**: Temporal trends and comparative analysis

## Technical Implementation
- **Data Pipeline**: SQL Server → Power BI Dataflows → Power BI Desktop
- **Data Volume**: 255,000+ records with incremental refresh
- **DAX Measures**: Advanced measures for risk analysis
- **Deployment**: Power BI Service with scheduled refresh

## Business Value
- Identifies high-risk demographic segments for targeted intervention
- Quantifies impact of credit scores, employment type, and loan purpose
- Provides temporal trend analysis for proactive risk management
- Enables data-driven product development and pricing strategies

## Getting Started
1. Download the Power BI Template (`.pbit`) from the `src` folder
2. Open in Power BI Desktop and connect to your loan data source
3. Follow the [Implementation Guide](docs/implementation-guide.md) for setup

## Documentation
- [Data Dictionary](docs/data-dictionary.md)
- [DAX Measures](docs/dax-measures.md)
- [Implementation Guide](docs/implementation-Andvisual-guide.md)
## Screenshots
### Overview Dashboard
![Overview Dashboard](assets/overview-dashboard.png)

### Demographics Dashboard
![Demographics Dashboard](assets/demographics-dashboard.png)

### Time Analysis Dashboard
![Time Analysis Dashboard](assets/time-analysis-dashboard.png)

## Technologies Used
- [Power BI](https://powerbi.microsoft.com/)
- [Microsoft SQL Server](https://www.microsoft.com/en-us/sql-server/)
- [Power BI Dataflows](https://docs.microsoft.com/en-us/power-bi/transform-model/dataflows/dataflows-introduction-self-service)
- [DAX](https://docs.microsoft.com/en-us/dax/)

## License
This project is for demonstration purposes only.
