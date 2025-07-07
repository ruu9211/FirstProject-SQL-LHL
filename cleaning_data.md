**What issues will you address by cleaning the data?**

1) The following issues were observed with the raw data and solved under one query as shown below:

* City column contains rows such as "(not set)" or "not available in demo dataset" replaced with 'Unknown City'.
* Incorrect city name attached to country (i.e. New York, Canada doesn't exist).
* Total transaction revenue column contains NULLs. 

Queries:

```sql
SELECT	CASE 
		WHEN country = 'Canada' AND city = 'New York' THEN 'United States'
            	ELSE country
        END AS country,
	CASE
		WHEN city IN ('(not set)','not available in demo dataset') THEN 'Unknown City'
		ELSE city
	END AS city,
        total_transaction_revenue
FROM 	all_sessions
WHERE 	total_transaction_revenue IS NOT NULL
```

2) Product Category column had a filed with unknown characters "{escCatTitle}". This was replaced with "Unknown"

Queries:

```sql
SELECT	CASE
      		WHEN country = 'Canada' AND city = 'New York' THEN 'United States'
      		ELSE country
    		END AS country,
    	CASE
      		WHEN city = 'not available in demo dataset' THEN 'Unknown'
      	ELSE city
    	END AS city,
    	REPLACE(v2_product_category, '${escCatTitle}', 'Unknown') AS cleaned_category,
	total_transaction_revenue
FROM 	all_sessions
WHERE 	total_transaction_revenue IS NOT NULL
```

3) Similarly, the product category column was formatted oddly in a way such as "Home/Office/Notebooks & Journals/". The column was cleaned to show category.

Queries:

```sql
SELECT	country,
    	city,
	    REGEXP_REPLACE(cleaned_category, '^Home/([^/]+)(/.*)?$', '\1') AS product_category,
		total_transaction_revenue
FROM 	CleanCategories
```

4) Total transaction revenue column was stored in micro units of currency. Therefore, it was converted to standard unit.

Queries:
```sql
SELECT	(total_transaction_revenue)/1000000 AS standard_total_revenue
FROM	all_sessions
WHERE 	total_transaction_revenue IS NOT NULL
```
5) Rounded output results to 2 decimal places to present average values better.

Queries:
```sql
SELECT	country,
    	city,
    	ROUND(AVG(total_ordered), 2) AS avg_total_ordered
FROM 	JoinedData
GROUP BY country, city
```