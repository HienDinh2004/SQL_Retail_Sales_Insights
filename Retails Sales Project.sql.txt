Retails Sales Project

– Query 01: Monthly Revenue Aggregation
CREATE OR REPLACE TABLE
  `fraud-project-466707.Retail_Sales_Dataset.iowa_summary` AS
SELECT
  county
 ,EXTRACT(YEAR FROM date) AS year,
 ,EXTRACT(MONTH FROM date) AS month,
 ,SUM(sale_dollars) AS revenue
FROM `bigquery-public-data.iowa_liquor_sales.sales`
GROUP BY county, year, month;

– Query 02: Top 5 Counties
SELECT county
     , SUM(revenue) AS total_revenue
FROM `fraud-project-466707.Retail_Sales_Dataset.iowa_summary`
GROUP BY county
ORDER BY total_revenue DESC
LIMIT 5;

– Query 03: Quarterly Seasonality
SELECT
  county,
  CASE
    WHEN month BETWEEN 1 AND 3 THEN 'Q1'
    WHEN month BETWEEN 4 AND 6 THEN 'Q2'
    WHEN month BETWEEN 7 AND 9 THEN 'Q3'
    ELSE 'Q4'
  END AS quarter,
  SUM(revenue) AS sum_rev
FROM `fraud-project-466707.Retail_Sales_Dataset.iowa_summary`
GROUP BY county, quarter
ORDER BY county, quarter;

– Query 04: YoY Revenue Growth
SELECT
  year
 ,SUM(revenue) AS total_revenue
 ,LAG(SUM(revenue)) OVER (ORDER BY year) AS prev_year_revenue
 ,ROUND(100 * (SUM(revenue) - LAG(SUM(revenue)) OVER (ORDER BY year))/ LAG(SUM(revenue)) OVER (ORDER BY year), 2) AS yoy_growth_pct
FROM `fraud-project-466707.Retail_Sales_Dataset.iowa_summary`
GROUP BY year
ORDER BY year;

– Query 05: Average Revenue per Transaction
SELECT
  county,
  ROUND(SUM(revenue) / COUNT(*), 2) AS avg_revenue_per_txn
FROM `fraud-project-466707.Retail_Sales_Dataset.iowa_summary`
GROUP BY county
ORDER BY avg_revenue_per_txn DESC
LIMIT 10;


– Query 06: Top 5 Stores by Revenue
SELECT
  store_number,
  SUM(sale_dollars) AS total_revenue
FROM `bigquery-public-data.iowa_liquor_sales.sales`
GROUP BY store_number
ORDER BY total_revenue DESC
LIMIT 5;

– Query 07: Price Distribution Buckets
SELECT
  CASE
    WHEN sale_dollars < 20 THEN '<$20'
    WHEN sale_dollars BETWEEN 20 AND 50 THEN '$20–50'
    WHEN sale_dollars BETWEEN 50 AND 100 THEN '$50–100'
    ELSE '>$100'
  END AS price_range,
  COUNT(*) AS txn_count
 ,ROUND(100 * COUNT(*) / SUM(COUNT(*)) OVER (), 2) AS pct_of_txns
FROM `bigquery-public-data.iowa_liquor_sales.sales`
GROUP BY price_range
ORDER BY pct_of_txns DESC;

– Query 08: Quarterly YoY Seasonality
WITH quarterly AS (
  SELECT
    EXTRACT(YEAR FROM date) AS year,
    CASE
      WHEN EXTRACT(MONTH FROM date) BETWEEN 1 AND 3 THEN 'Q1'
      WHEN EXTRACT(MONTH FROM date) BETWEEN 4 AND 6 THEN 'Q2'
      WHEN EXTRACT(MONTH FROM date) BETWEEN 7 AND 9 THEN 'Q3'
      ELSE 'Q4'
    END AS quarter
   ,SUM(sale_dollars) AS revenue
  FROM `bigquery-public-data.iowa_liquor_sales.sales`
  GROUP BY year, quarter
)
SELECT
  q1.year
 ,q1.quarter
 ,q1.revenue AS current_q_revenue,
  q2.revenue AS last_year_q_revenue,
  ROUND(100 * (q1.revenue - q2.revenue) / q2.revenue, 2) AS yoy_q_growth_pct
FROM quarterly q1
LEFT JOIN quarterly q2
  ON q1.quarter = q2.quarter
  AND q1.year = q2.year + 1
ORDER BY q1.year, q1.quarter;










