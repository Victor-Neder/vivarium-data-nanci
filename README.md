# Data Analysis and Dashboard - Nanci do Nascimento Vivarium (IPEN-USP)

## 📖 Description

This project started when I saw there was a surplus of animals (too many animals) during daily work at the Nanci do Nascimento Vivarium (IPEN-USP). The first idea was to optimize the population, but this created a need to prove, using data analysis, that it was possible to reduce the number of animals and still keep a safe margin.

## 🎯 Main Objective

The main goal is to show that this optimization can lead to direct benefits, like reducing operational costs (feed, bedding) and, most importantly, reducing the workload for the technical team.

I will analyze historical animal request data to find demand patterns (by strain, age, and seasonality) and provide insights to support a strategy to optimize the vivarium's population, aiming to reduce costs and workload.

## 🖥️ Technologies Used

   * **Languages:** Python, SQL
   * **Python Libraries:** Pandas, NumPy, Matplotlib, Seaborn, SQLAlchemy
   * **Database:** PostgreSQL
   * **Cloud:** Google Cloud Platform (GCP) - specifically Cloud SQL for PostgreSQL
   * **BI & Visualization:** Microsoft Power BI
     

⚙️ Methodology and Steps

1.  **ETL and Data Cleaning:**
   * Done in the Jupyter notebook (exploratory_data_analysis.ipynb).
   * Load the data from the vivarium_data.csv file.
   * Standardize column names (lowercase, rename to English).
   * Clean and standardize text data (strains, months - lowercase, trim spaces).
   * Remove irrelevant columns or columns with too much missing data (like 'peso').
   * Handle missing values in the 'idade' (age) column.
   * Create a standard age_days column from inconsistent formats (weeks, months, days, ranges).
   * Create numeric (month_num) and translated (month_en) columns for the months.
   * The final result is a clean DataFrame (df_cleaned_vivarium_data.csv) ready for analysis.
     

 2.   **Exploratory Data Analysis (EDA):**

   * Done in the Jupyter notebook (exploratory_data_analysis.ipynb).
   * Using Pandas for aggregations and descriptive stats.
   * Creating charts with Matplotlib and Seaborn to find key patterns:
     * **Strain Popularity:** Finding the most and least requested strains (Ordered Bar Chart).
      * **Age Profile:** Analyzing the age distribution of animals when they are requested (Histogram, Boxplot).
      * **Seasonality:** Checking for demand patterns throughout the months (Monthly Bar/Line Chart).
      * **Time Trend:** Analyzing how demand has changed over the years, by strain (Line/Dot Chart).
        

  3.   **Database Structure:**

   * Defining the schema (structure) for a relational table in PostgreSQL to store the clean data.
   * Creating the table in the database, setting the correct data types for each column.
   * Making the database a single, reliable source for the clean data.
     

   4.  **Infrastructure Setup:**

   * Setting up a managed PostgreSQL instance using Google Cloud SQL
   * Configuring security (network permissions) for safe access.
   * Importing the clean data from the CSV file into the Cloud SQL table using Python (Pandas + SQLAlchemy).
     

  5.   **Dashboard Development:**

   * Connecting Microsoft Power BI directly to the PostgreSQL instance in the Google Cloud.
   * Creating an interactive dashboard with:
     * **KPIs (Key Indicators):** Cards showing main numbers (Total Samples, Top Strain, Average Age, Change vs. Last Year).
     * **Dynamic Charts:** Bar charts, line charts, and a histogram that show the insights from the EDA.
     * **Interactive Filters:** Slicers to explore data by Year and Strain.
     * **DAX Measures:** Creating custom calculations for advanced KPIs.
       

## 📊 Main Insights from the Analysis

   * **Demand Concentration:** A large majority of requests (~78%) are focused on only three main strains (balb/c nude, balb/c, c57bl-6).
   * **Low-Demand Strains:** Found strains with very low requests and/or no recent orders (lit/lit, lit/scid, scid, swiss). This suggests we can optimize by using on-demand breeding or buying from outside.
   * **Age Profile:** The main demand is for young adult animals, around 40 to 70 days old, with clear peaks that might show specific needs for each strain or experiment type.
   * **Clear Seasonality:** Demand has big peaks at the start of the year and sharp drops during academic holidays (July/December). This allows for better planning of resources and production.
     

## 🖥️ Visualization (Dashboard)
![Screenshot Main Dashboard](dashboards/screenshot_dashboard.png) 


# 🚀 Future Updates

   * **Pipeline Automation:** Implement an automatic flow where new requests (from a form) are put directly into the PostgreSQL database and updated in Power BI.
