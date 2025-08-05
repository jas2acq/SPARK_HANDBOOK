# SPARK_HANDBOOK
A practical guide to Apache Spark with clear, example-driven workflows for data engineering and analytics. Covers RDDs, DataFrames, Spark SQL, and performance tuning.


# Data Background

Our fictional company, "Global Gadgets," sells electronics and accessories online. We have three main data sources that we need to integrate:

- **customers.csv**: Contains basic information about our registered users. Some entries might have missing or inconsistent data.
- **products.json**: A log of product information, including product names, prices, and categories. This data is semi-structured.
- **orders_parquet**: A log of all customer purchases, including the order_id, customer_id, product_id, and quantity. This is our primary transactional data, and it's already in an efficient, columnar format (Parquet).

The ETL process will combine these datasets to create a single, unified view of our sales, which will be used for downstream business intelligence and reporting.
