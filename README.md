# **Final-Project-Transforming-and-Analyzing-Data-with-SQL**

## **Project/Goals**
This project involved analyzing an e-commerce dataset to support better decision-making across product strategy and regional sales efforts. The dataset included product details, transaction revenue, web session activity, and geographic data such as country and city. Tools such as PostgreSQL and pgAdmin were utilized to clean and transform the data, handle missing values across multiple entities and duplicate records caused by complex joins. Thereafter an exploratory analysis was performed to understand where revenue is coming from, which cities and countries drive the most engagement, and how product sales differ across regions.

## **Process**
## Step 1: Understanding the Dataset
* Explored the following datasets: all_sessions, products, sales_by_sku, analytics, and sales_report.
* Reviewed the structure and purpose of the datasets to get an understanding of the business model.
* Identified relationships between the datasets and established primary and foreign keys.

## Step 2: Data Cleaning
* Filtered out invalid or incomplete values.
* Ensured data type consistencies.
* Removed duplicate values and ensure datasets were distinct.

## Step 3: Optimization and Validation
* Ensured joins between session and product tables did not inflate metrics.
* Verified that total sums matched expected business figures or control totals from raw data.
* Investigated discrepancies immediately and refined join conditions or filters.

## Step 4: Exploratory Data Analysis (EDA)
* Aggregated total and average revenue by city and country.
* Identified top-selling products by region and product category.
* Calculated average quantity ordered per visit across locations.
* Demand-to-stock ratio was calculated to understand product performance and inventory management. 

## Results
The analysis revealed key insights such as:

* Revenue varied significantly across cities and countries, highlighting high-priority markets.
* Customers in certain locations purchased more products per visit, indicating stronger engagement.
* Clear patterns emerged in product categories preferred by different regions, guiding localized marketing.
* Top-selling products by city and country uncovered opportunities for tailored inventory and promotions.
* Total revenue contributions by region helped prioritize resource allocation.
* Marketing channel analysis identified which channels drove the most revenue, focusing marketing efforts.
* Matching SKUs showed which products generated the most revenue and how long users spent on-site during those purchases, offering clues to improve customer experience.
* Inventory demand analysis categorized products as overstocked, understocked, or balanced, enabling smarter stock management.
* Cleaning and standardizing location data significantly improved the accuracy of geographic insights.

## Challenges 
* Dealing with missing and inconsistent location data (e.g., (not set) and placeholder values).
* Cleaning and standardizing product names and location fields to avoid grouping errors.
* Defining and applying business logic for categorizing inventory demand ratios.
* Handling null and incomplete values in critical fields like revenue and quantity.
* Extracting actionable insights from raw session and transaction data.

## Future Goals
* Further clean the datasets to establish relationships and link the data effectively.
* Incorporate visual diagrams to better visualize and interpret data.
* Analyze customer feedback sentiment to better understand product perception.
* Evaluate the impact of different social engagement types on sales and customer activity.








