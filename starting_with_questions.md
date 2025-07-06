Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**

```sql 
WITH CTE1 AS (
			SELECT	CASE 
						WHEN country = 'Canada' AND city = 'New York' THEN 'United States'
            			ELSE country
        				END AS country,
					CASE
					WHEN city IN ('(not set)','not available in demo dataset') THEN country
					ELSE city
					END AS city,
        			total_transaction_revenue
			FROM 	all_sessions
			WHERE 	total_transaction_revenue IS NOT NULL
			)
SELECT	country,
    	city,
    	SUM(total_transaction_revenue) / 1000000 AS total_revenue
FROM 	CTE1
GROUP BY country, city
ORDER BY total_revenue DESC;
```

Answer:

![answer_5_1](./images/question_1.png)



**Question 2: What is the average number of products ordered from visitors in each city and country?**


```sql
SELECT	all_s.country,
		CASE
			WHEN all_s.city IN ('(not set)','not available in demo dataset') THEN all_s.country
			ELSE all_s.city
			END AS city,
		ROUND(AVG(total_ordered),2) AS avg_total_ordered
FROM	sales_by_sku AS sales
		JOIN all_sessions AS all_s
		ON sales.product_sku = all_s.product_sku
WHERE 	all_s.city IS NOT NULL OR all_s.country IS NOT NULL
GROUP BY all_s.country, city
ORDER BY avg_total_ordered DESC;
```

Answer:

![answer_5_2](./images/question_2.png)




**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:



Answer:





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:



Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







