What are your risk areas? Identify and describe them.

1. The below query was executed to determine the primary key for the e-commerce dataset. The goal is to identify unique identifiers as it cannot contain nulls or duplicates.

```sql
SELECT sku, COUNT(*) AS unique_identifiers
FROM products 
GROUP BY sku 
HAVING COUNT(*) > 1;
```

2. The below query was executed to check if joining sales_by_sku and all_sessions tables would result in duplicates which could impact the average result. The result yielded to count > 1 confirming the duplicates and need to use DISTINCT. 

```sql
SELECT 	product_sku, COUNT(*) AS count
FROM 	all_sessions
GROUP BY product_sku
ORDER BY count DESC;
```

3. The values in columns for product refund, product quantity, and product price doesn't add up to the product revenue column. The below query was used to filter out the NULLs to visually see the discrepancy.

```sql
SELECT	COUNT(product_refund_amount) AS refund_count,
		COUNT(product_quantity) AS quantity_count,
		COUNT(product_price) AS price_count,
		COUNT(product_revenue) AS revenue_count
FROM	all_sessions
WHERE	product_refund_amount IS NOT NULL
		OR product_quantity IS NOT NULL
		OR product_price IS NOT NULL
		OR product_revenue IS NOT NULL;
```

Followed by the following query:

```sql
SELECT	product_quantity, product_price, product_revenue
FROM	all_sessions
WHERE	product_quantity IS NOT NULL
		AND product_price IS NOT NULL
		AND product_revenue IS NOT NULL;
```