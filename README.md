# Live API Data Integration: Real-Time Dashboards with Python & Power BI

## 📌 Project Overview
This project focuses on building a **live, interactive dashboard** that displays important global statistics such as health, education, employment, and other key indicators.  

- **Data Source**: Public API regularly updated with the latest information  
- **Data Processing**: Python script automatically fetches and processes data for analysis  
- **Integration**: Python script connected directly to Power BI for live data connection  
- **Outcome**: Power BI dashboard refreshes automatically whenever new data is available, eliminating manual updates  

The dashboard provides **easy-to-understand visuals** (charts, graphs, trend lines) to help users explore patterns across countries and regions.

---

## ⚙️ Workflow
1. **Fetch Data**: Python script retrieves fresh data from the API.  
2. **Process Data**: Clean and prepare data for analysis.  
3. **Connect to Power BI**: Establish live connection for real-time updates.  
4. **Visualize**: Build interactive dashboards with charts, graphs, and trend analysis.  

---

## 📊 Data ETL Process (API Data.ipynb)
The ETL (Extract, Transform, Load) process is handled by the `API Data.ipynb` Jupyter notebook, which automates data fetching, processing, and preparation for analysis and visualization.

### Key Steps in the ETL Pipeline:
1. **Extract Countries Data**:
   - Fetches a list of all countries from the World Bank API (`https://api.worldbank.org/countries?format=json&per_page=300`).
   - Processes country metadata, including region, income level, and lending type.
   - Cleans and renames columns for consistency (e.g., `iso2Code` to `country_id`).
   - Filters out aggregates to focus on individual countries.

2. **Extract Indicators Metadata**:
   - Retrieves a comprehensive list of all available indicators from the World Bank API.
   - Paginates through 525 pages to collect over 16,000 indicators.
   - Saves the full indicator list to `final_df.csv` for reference.

3. **Define Indicator Groups**:
   - Organizes indicators into thematic categories for targeted analysis:
     - **Economic Activity & Growth**: GDP growth, GDP per capita.
     - **Labour Market Indicators**: Unemployment rates, labour force.
     - **Trade & Globalization**: Exports, imports.
     - **Poverty & Inequality**: Poverty headcount, Gini index.
     - **Environmental Indicators**: Renewable energy, forest area.
     - **Health Indicators**: Life expectancy, immunization rates, health expenditure, etc.
     - **Technology Indicators**: Internet usage, mobile subscriptions.

4. **Fetch Time-Series Data for Indicators**:
   - For each indicator in the defined groups, fetches historical data from 2016 onwards (filtering `year > 2015`).
   - Handles pagination to collect all available data points.
   - Includes rate limiting (0.3s delay between requests) to respect API limits.
   - Normalizes JSON responses into structured DataFrames.

5. **Transform & Merge Data**:
   - Merges each category's data with the countries DataFrame using `country_id`.
   - Drops unnecessary columns (e.g., `indicator_id`, `name`, `id`) for cleaner datasets.
   - Prepares data for analysis by ensuring consistent structure.

6. **Load Data to CSVs**:
   - Saves processed data for each category to separate CSV files:
     - `economic.csv`
     - `labour_market.csv`
     - `trade.csv`
     - `poverty.csv`
     - `environment.csv`
     - `health.csv`
     - `technology.csv`

7. **Exploratory Data Analysis (EDA)**:
   - Performs correlation analysis on health indicators using a heatmap.
   - Generates regression plots to explore relationships (e.g., health expenditure vs. life expectancy).
   - Visualizes insights directly in the notebook for quick validation.

### Technical Details:
- **API Source**: World Bank Open Data API (https://data.worldbank.org/).
- **Data Scope**: Global coverage for countries, with time-series data from 2016 to the latest available year.
- **Libraries Used**: `requests` for API calls, `pandas` for data manipulation, `seaborn` and `matplotlib` for visualizations.
- **Output**: Clean, category-specific CSV files ready for import into Power BI or other analysis tools.
- **Automation**: The notebook can be run periodically to fetch the latest data, ensuring real-time updates.

This ETL process ensures data integrity, handles API rate limits, and structures data optimally for downstream dashboard creation.

---

## 🎯 Key Questions Addressed

### 1. Understand the Overall Economic & Social Landscape
- Average **GDP per capita** → measure of individual economic well-being  
- Average **trade value** → activity in international markets  
- Average **health spending (% of GDP)** → national health investment priorities  
- Average **GDP growth rate** → overall economic momentum  
- **Forest area proportion** → impact on land use, agriculture, and natural resources  

These metrics provide foundational context before deeper analysis.

---

### 2. Compare Health Spending Patterns Across Regions
- Compare **average health spending (% of GDP)** across world regions  
- Highlight **regional disparities** and differences in health outcomes or priorities  

---

### 3. Analyze Trends in Key Socio-Economic Indicators
Track changes over time in:  
- Forest area  
- Mobile subscriptions  
- Internet subscriptions  
- GDP  
- Renewable energy use  
- Unemployment  

These trends reveal whether countries are moving in positive or negative directions.

---

### 4. Evaluate Impact of Internet Access on Immunization Awareness
- Assess relationship between **internet penetration** and **immunization rates**  
- Explore how digital connectivity improves **health information access** and **public engagement**  

---

### 5. Assess Role of Internet Access in Reducing Unemployment
- Investigate whether expanding **internet penetration** contributes to lowering unemployment levels  

---

### 6. Identify Underperforming Countries in Poverty Reduction
- Pinpoint **bottom 10 countries** with least progress in reducing poverty  
- Guide policymakers, NGOs, and donors to focus resources on struggling nations  

---

### 7. Identify Top-Performing Countries in Poverty Reduction
- Highlight **top 10 countries** with most progress in reducing poverty  
- Extract lessons from successful policies and strategies  

---

### 8. Examine Interrelationships Among Health Indicators
- Explore correlations between:  
  - Health expenditure  
  - Life expectancy  
  - Immunization rates  
  - Child mortality  
  - Disease burden  

Understanding these relationships helps shape **integrated health strategies**.

---

### 9. Investigate Relationship Between Government Health Spending & Life Expectancy
- Use **trend line analysis** to explore whether increased health expenditure improves life expectancy  
- Determine if spending alone is effective or if other factors must be addressed  

---

## 🚀 Outcomes
- Real-time, automated dashboards  
- Actionable insights for policymakers, NGOs, and researchers  
- Evidence-based strategies for improving health, education, and poverty reduction  

---
"# Live-API-Data-Integration-Real-Time-Dashboards-with-Python-Power-BI" 
