# Men's T-Shirt Sales Performance Dashboard

### Dashboard Link : https://app.powerbi.com/links/_CN9MweMWt?ctid=e9f53682-9dc4-428b-ba7b-b55c3de07e9b&pbi_source=linkShare

## Problem Statement

This Power BI dashboard focuses on analyzing the sales performance of men's t-shirts. The objective is to provide key insights into sales trends, profitability, discount effectiveness, and brand performance. By visualizing crucial metrics such as total sales, profit margins, average prices, and discount percentages, this report aims to help retail stakeholders (e.g., product managers, sales teams, marketing departments) make data-driven decisions to optimize pricing strategies, improve inventory management, identify top-performing brands, and enhance overall profitability.

## Dataset

The primary dataset for this analysis is derived from **`Men+Tshirt.csv`**, containing detailed information about individual t-shirt products and their sales attributes. Prior to loading into Power BI, this data underwent significant cleaning and preparation in an **Azure SQL Database**.

## Steps Followed

1.  **Data Acquisition & Preparation (Azure SQL & Power BI):**
    * **Azure SQL Data Cleaning:** The raw sales data was initially imported into an Azure SQL Database. SQL queries and procedures were utilized for extensive data cleaning, including:
        * Handling missing values.
        * Standardizing text fields (e.g., brand names, categories).
        * Removing duplicates or irrelevant entries.
        * Ensuring data consistency and integrity at the database level.
    * **Connecting to Power BI:** After cleaning in Azure SQL, the refined data was directly connected to Power BI Desktop using the "Get Data" -> "Azure SQL Database" connector. This ensured a clean and robust data source for further analysis.
    * **Loading CSV:** The `Men+Tshirt.csv` file was also loaded, possibly as a supplementary source or the main clean source after the SQL cleaning process, depending on the architecture.

2.  **Data Profiling (Power Query Editor):**
    * Within Power Query Editor, the loaded tables were profiled to understand their structure and content.
    * "Column quality," "Column distribution," and "Column profile" options (under the "View" tab) were actively used to check for data types, errors, empty values, and unique/distinct value counts across all columns.
    * "Column profiling based on entire dataset" was selected for a comprehensive view of data quality.

3.  **Data Transformation (Power Query):**
    * **Data Type Assignment:** Ensured all columns had correct data types (e.g., `Decimal Number` for prices/percentages, `Text` for brands/names).
    * **Handling Blanks/Errors:** Addressed any residual blank values or errors that might have surfaced after initial SQL cleaning, using Power Query's capabilities (e.g., "Remove Rows with Errors," "Replace Values").
    * **(Optional - Add your specific transformations here):** If any calculated columns were done in Power Query (M Language) before DAX, describe them here (e.g., creating price tiers, combining categories).

4.  **Data Modeling:**
    * The data model was established based on the imported `Men Tshirt` table.
    * (Assumption: If there were other related tables, relationships were set up appropriately to ensure data integrity and filter context propagation.)

5.  **DAX Calculations:**
    The following key measures and calculated columns were created using DAX to derive actionable insights:

    * **`Profit %` (Calculated Column):** This column was created to assign a random profit percentage to each transaction/product, simulating potential profit margins for analysis.
        ```dax
        Profit % = RANDBETWEEN(2,17)

    * **`Cost Price` (Measure):** Calculates the estimated cost price of each t-shirt based on its sales price and the assigned profit percentage.
        ```dax
        Cost Price = DIVIDE(100 * 'Men Tshirt'[Sales Price], 100 + 'Men Tshirt'[Profit %])
        ```
    * **`Discount %` (Measure):** Calculates the discount percentage applied to each t-shirt, providing insight into pricing strategies.
        ```dax
        Discount % = DIVIDE('Men Tshirt'[Marked Price] - 'Men Tshirt'[Sales Price], 'Men Tshirt'[Marked Price]) * 100

6.  **Dashboard Design & Visualization (Multi-Page Report):**
    The report is structured into two distinct, interactive pages to provide a focused and comprehensive view of the data.

    * **Page 1: Available Brands Page**
        * This page serves as an initial overview or selection hub.
        * It likely features a clear listing or visual representation of all `Available Brands` in the dataset, possibly in a simple list visual.

    * **Page 2: Details Page**
        * This page delves into detailed analytical insights, comparing top and bottom performing brands across various metrics.
        * **Stacked Bar Chart:** Visualizes the `Top 5 Brands by Average Discount Percentage`, highlighting how discounts are distributed among leading brands.
        * **Donut Chart:** Illustrates the `Top 5 Brands by Highest Number of Varieties`, showing which brands offer the most product diversity.
        * **Ribbon Chart:** Displays the `Top 5 Brands by Highest Average Sales Price`, allowing for a clear comparison of premium pricing strategies.
        * **Area Chart:** Shows the `Top 5 Brands by Highest Average Profit Percentage`, indicating the most profitable brands based on the simulated profit margins.
        * **Pie Chart:** Highlights the `Bottom 5 Brands by Average Profit Percentage`, identifying brands that are less profitable or require strategic intervention.

## Dashboard Snapshots

Here are visual representations of the key pages within the Men's T-Shirt Sales Performance Dashboard.

**Page 1 - Available Brands Page:**
![Available Brands Page]<img width="1250" height="638" alt="Image" src="https://github.com/user-attachments/assets/1b11eacc-c277-42ec-83bc-890acea9f6d3" />


**Page 2 - Details Page:**
![Details Page - Visuals]<img width="1255" height="637" alt="Image" src="https://github.com/user-attachments/assets/55376a07-2f65-4344-a525-9744bb52681b" />
## Key Insights

This dashboard enables critical insights for optimizing men's t-shirt sales operations:

* **Overall Performance:** Quick understanding of total sales revenue, profit, and average pricing.
* **Brand Performance:** Identification of top-performing and underperforming brands in terms of sales, profit, and discount levels.
* **Profitability Drivers:** Analyzing the impact of discounts on sales volume and profit margins to fine-tune pricing strategies.
* **Product Assortment:** Insights into the variety of products offered by different brands and their contribution to overall sales.
* **Sales Trends:** Monitoring sales performance over time to identify seasonal patterns or the impact of marketing campaigns.
* **Cost & Revenue Analysis:** Understanding the relationship between cost, sales, and profit.

## Technologies Used

* **Microsoft Power BI Desktop:** For data modeling, DAX calculations, and interactive dashboard creation.
* **Azure SQL Database:** For robust data storage, initial cleaning, and querying.
* **Power Query (M Language):** For advanced data extraction, transformation, and loading (ETL) within Power BI.
* **DAX (Data Analysis Expressions):** For creating complex measures and calculated columns to derive business logic and performance metrics.
* **CSV Files:** As a source for the raw product and sales data.

---
