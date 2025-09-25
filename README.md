Agriculture Dashboard Project Wiki
1. Project Overview

India’s agricultural sector is vital for the economy, but managing agricultural data is complex and fragmented. This project aims to create an interactive data visualization platform that integrates agricultural data from different states and districts.

Goals:

Provide insights into crop production, yield, and area under cultivation.

Help farmers make informed decisions about crop selection.

Assist policymakers in resource allocation and monitoring.

Enable researchers to analyze trends and agricultural performance.

Stakeholders & Use Cases:

Farmers: Explore historical crop performance, regional productivity, and optimize crop choices.

Policymakers: Identify low-yield regions and plan interventions or subsidies.

Researchers: Analyze crop trends, climate impacts, and explore innovation opportunities.

2. Project Setup

Required Tools & Technologies:

Python (Pandas, NumPy, Matplotlib/Seaborn/Plotly)

MySQL Database

Power BI Desktop

Streamlit (for future web dashboard)

Folder Structure:

agriculture_dashboard/
│
├─ data/                 # Raw and cleaned CSV files
│   └─ ICRISAT-District Level Data_clean.csv
│
├─ scripts/              # Python scripts
│   ├─ data_cleaning.py
│   ├─ db_load.py
│   ├─ eda_visualization.py
│   └─ forecasting.py
│
└─ README.md

3. Data Cleaning

Cleaned column names to lowercase and replaced spaces with underscores.

Stripped whitespace and normalized case for state_name and dist_name.

Converted numeric columns (area, production, yield) to numeric type.

Recalculated yields (production/area) for accuracy.

Dropped rows with missing year or state_name.

Saved cleaned CSV:
data/ICRISAT-District Level Data_clean.csv

4. Database Loading (MySQL)

Database Name: Agriculture_dashboard

Table Name: agriculture_data

Python Script: db_load.py

Reads the cleaned CSV.

Connects to MySQL using credentials:

MYSQL_USER = "pavankumar"
MYSQL_PASSWORD = "PAva19@#"
MYSQL_DB = "Agriculture_dashboard"
MYSQL_HOST = "localhost"


Creates the table dynamically based on CSV columns.

Inserts all rows into the database.

✅ Database now contains 16,146 rows and 81 columns.

5. Exploratory Data Analysis (EDA)

Visualizations are generated using Python (Plotly / Seaborn / Matplotlib).

Example charts created:

Top 7 rice-producing states (Bar plot)

Top 5 wheat-producing states (Bar + Pie chart)

Oilseed production by top 5 states

Trend of sugarcane production over 50 years (Line plot)

Rice vs. Wheat production comparison

Millet, Sorghum, Groundnut, Soybean production analysis

Interactive filters for Year, State, and Crop Type implemented.

6. Power BI Visualizations

Loaded cleaned CSV directly into Power BI.

Visuals Used:

Map / Filled Map: shows crop production/yield distribution by state or district

Location: state_name or dist_name

Size: rice_production_1000_tons (or other crops)

Color saturation: rice_yield_kg_per_ha

Tooltip: state_name, area, production, yield

Line Charts: Crop trends over time (e.g., rice production last 50 years)

Bar / Column Charts: Compare production across states

Donut Charts: Share of crop production by top states

Slicers: Interactive filters for Year, Crop Type, State

Interactivity:

Selecting a state updates all visuals.

Year slicer allows trend analysis for specific years.

Crop slicer allows switching between crops.

7. Next Steps

Implement Forecasting: Predict crop yields using ML models.

Build a Streamlit web dashboard for end-users.

Integrate SQL queries in Power BI to fetch data dynamically.
