**I. Introduction**
__________________________________________
This projec analyzes retail liquor sales data for the state of Iowa (public dataset on BigQuery) tto uncover regional performance, customer spending patterns, and seasonal trends using SQL.

**II. Project Objectives**
__________________________________________
- Aggregate monthly and quarterly revenue by county.

- Identify top-performing counties and stores.

- Measure year-over-year (YoY) growth and seasonal effects.

- Analyze average revenue per transaction and price distribution.

- Provide actionable insights for marketing and inventory planning.

**III. Requirements**
__________________________________________
- Google Cloud Platform account
- Project on Google Cloud Platform
- Google BigQuery API enabled
- SQL query editor or IDE

**IV. Dataset Access**
__________________________________________
The retail sales dataset is stored in a public Google BigQuery dataset. To access the dataset, follow these steps:

- Log in to your Google Cloud Platform account and create a new project.
- Navigate to the BigQuery console and select your newly created project.
- In the navigation panel, select "Add Data" and then "Search a project".
- Enter the project ID "bigquery-public-data.iowa_liquor_sales.sales" and click "Enter".

**V. Exploring the Dataset**
__________________________________________
In this project, I will write 08 query in Bigquery base on Google Analytics dataset

**Query 01: Monthly Revenue Aggregation**
- Code
<img width="1014" height="656" alt="image" src="https://github.com/user-attachments/assets/e93d7bf8-efb9-48ea-a91a-4d25cc7c6bc8" />

- Result
  <img width="1104" height="241" alt="image" src="https://github.com/user-attachments/assets/0471a751-02ac-40d4-9430-75cd478729c5" />
  

**Query 02: Top 5 Counties**

- Code
  
  <img width="903" height="258" alt="image" src="https://github.com/user-attachments/assets/c837395c-6a4a-43a6-b5be-5ad8922a668d" />

- Result
  
<img width="801" height="203" alt="image" src="https://github.com/user-attachments/assets/be998091-edf7-4fc6-b839-1a1a29102f41" />

**Query 03: Quarterly Seasonality**

- Code

<img width="784" height="337" alt="image" src="https://github.com/user-attachments/assets/a4429bc3-7c32-4c1b-aeba-0c6adaa3de11" />

- Result

<img width="1404" height="297" alt="image" src="https://github.com/user-attachments/assets/50f418cc-16b3-4a7d-b6b1-9eaf66f53d94" />

**Query 04: YoY Revenue Growth**

- Code

<img width="1404" height="215" alt="image" src="https://github.com/user-attachments/assets/67a1d27a-b148-4779-8fa6-c300f8dd649d" />

- Result

<img width="1372" height="409" alt="image" src="https://github.com/user-attachments/assets/bc2e58f5-0ffe-49be-a87b-ac7829fd7ab1" />

**Query 05: Average Revenue per Transaction**

- Code

<img width="1310" height="596" alt="image" src="https://github.com/user-attachments/assets/eb7503b6-624f-4602-9eba-d2d387233af6" />

- Result

<img width="1361" height="383" alt="image" src="https://github.com/user-attachments/assets/9e863442-7805-47fc-b48d-0d963ad72fbe" />

**Query 06: Top 5 Stores by Revenue**

- Code
<img width="1320" height="374" alt="image" src="https://github.com/user-attachments/assets/14b6cddb-faa9-4833-a018-bef988da04d6" />

- Result

<img width="1395" height="347" alt="image" src="https://github.com/user-attachments/assets/728410b0-b2ba-459b-934e-1ad35372298a" />

**Query 07: Price Distribution Buckets**

- Code
<img width="911" height="396" alt="image" src="https://github.com/user-attachments/assets/5f77cee4-28ee-4415-96fd-383a66136dc8" />

- Result
<img width="884" height="204" alt="image" src="https://github.com/user-attachments/assets/53b6f12b-c7d6-4acc-b416-f6d027cc39b0" />

**Query 08: Quarterly YoY Seasonality**

- Code
<img width="661" height="488" alt="image" src="https://github.com/user-attachments/assets/4182c0b9-7d3d-4e53-95d4-c43d09f2d433" />
<img width="701" height="468" alt="image" src="https://github.com/user-attachments/assets/347a8902-8642-45a1-8383-6dae38632651" />

- Result
<img width="727" height="187" alt="image" src="https://github.com/user-attachments/assets/24e47c23-d3f4-4754-830c-1041b0bfa838" />

**VI. Key Insights**
__________________________________________
- County Revenue Concentration: The top 5 counties contribute over 60% of total state revenue, indicating high regional concentration and priority areas for marketing.

- Seasonal Spike in Q4: Average Q4 revenue is 25% higher than average of Q1–Q3, suggesting that holiday promotions and inventory stocking should focus on year-end periods.

- YoY Growth Trend: Statewide revenue grew by 12% from 2019 to 2020, signaling strong market expansion that stakeholders can leverage for growth projections.

- High-Value Transactions: The top 10 counties by average revenue per transaction show an average spend of $45, identifying higher-income customer segments for premium offerings.

- Store Performance Leaders: Top 5 stores account for 15% of all sales, highlighting critical retail locations requiring optimized staffing and inventory management.

- Price Sensitivity: 40% of transactions fall under the <$20 bucket, indicating a substantial low-price segment where targeted promotions could drive volume.

- Post-Pandemic Recovery: Q2 of 2020 saw a 30% increase vs Q2 of 2019, reflecting strong recovery after initial COVID-19 impact—useful for future crisis response planning.



















