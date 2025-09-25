---

# **Agriculture Dashboard Project **

## **1. Project Overview**

India’s agriculture is vital for the economy, but managing agricultural data is challenging due to its fragmented nature. This project creates an **interactive dashboard** to visualize agricultural data across states and districts, helping stakeholders make informed decisions.

**Goals:**

* Provide insights into crop production, yield, and cultivation area.
* Enable farmers to optimize crop selection.
* Assist policymakers in resource allocation and monitoring.
* Support researchers in analyzing trends and innovation opportunities.

**Stakeholders & Use Cases:**

* **Farmers:** Explore historical crop data, regional productivity, and optimize crop choices.
* **Policymakers:** Identify low-yield regions, plan interventions, and manage crop risk.
* **Researchers:** Analyze crop trends, climate impact, and evaluate agricultural innovations.

---

## **2. Project Setup**

**Technologies Used:**

* Python (Pandas, NumPy, Matplotlib, Seaborn, Plotly)
* MySQL
* Power BI
* Streamlit (for future deployment)

**Folder Structure:**

```
agriculture_dashboard/
│
├─ data/                 # Raw & cleaned CSV
│   └─ ICRISAT-District Level Data_clean.csv
│
├─ scripts/              # Python scripts
│   ├─ data_cleaning.py
│   ├─ db_load.py
│   ├─ eda_visualization.py
│   └─ forecasting.py
│
└─ README.md
```

---

## **3. Data Cleaning**

* Standardized column names (lowercase, underscores instead of spaces).
* Stripped whitespace and normalized `state_name` & `dist_name`.
* Converted numeric columns (`area`, `production`, `yield`) to numbers.
* Recalculated yields (`production ÷ area`) where necessary.
* Dropped rows missing `year` or `state_name`.
* **Cleaned CSV saved:** `data/ICRISAT-District Level Data_clean.csv`

---

## **4. Database Loading (MySQL)**

* **Database:** `Agriculture_dashboard`
* **Table:** `agriculture_data`

**Python Script:** `db_load.py`

* Loads the cleaned CSV.
* Connects to MySQL using credentials:

```python
MYSQL_USER = "pavankumar"
MYSQL_PASSWORD = "PAva19@#"
MYSQL_DB = "Agriculture_dashboard"
MYSQL_HOST = "localhost"
```

* Dynamically creates the table and inserts all rows.
* ✅ Successfully loaded **16,146 rows** with **81 columns**.

---

## **5. Exploratory Data Analysis (EDA)**

Visualizations created using **Python (Plotly/Seaborn/Matplotlib)**:

* **Bar Charts:** Top 7 rice-producing states, Top 5 wheat-producing states
* **Pie/Donut Charts:** Share of wheat production by top states
* **Line Charts:** Sugarcane trends over 50 years, Rice vs Wheat production
* **Scatter Plots:** Area vs Production correlations
* **Filters:** Year, State, Crop Type for interactive exploration

---

## **6. Power BI Visualizations**

**Steps:**

1. Load the cleaned CSV into Power BI.
2. Create visuals:

   * **Map/Filled Map:** Crop production/yield distribution

     * **Location:** `state_name` or `dist_name`
     * **Size:** `production` column
     * **Color:** `yield` column
     * **Tooltip:** Area, Production, Yield
   * **Line Chart:** Crop trends over time
   * **Bar/Column Chart:** Compare crop production across states
   * **Donut Chart:** Share of production by top states
   * **Slicers:** Year, Crop Type, State for interactive filtering

**Interactivity:**

* Selecting a state updates all visuals.
* Year slicer allows analysis of specific years.
* Crop slicer allows switching between crops.

---

## **7. Next Steps**

* Implement **forecasting models** to predict crop yields.
* Build a **Streamlit web dashboard** for interactive access.
* Integrate **dynamic SQL queries** in Power BI for live data updates.

---

