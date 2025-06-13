# Notes – Day 1: Data Engineering Masterclass by Darshil Parmar

## 1. What Does a Data Engineer Actually Do?

A data engineer builds and maintains systems that collect, process, and store data. Responsibilities include:

- Building and managing data pipelines (ETL/ELT)
- Working with databases and data warehouses
- Using big data tools like Apache Spark, Hadoop
- Leveraging cloud platforms such as AWS, GCP, or Azure

> Example: A data engineer might build a pipeline that collects daily sales data from a store's POS system, transforms it into a usable format, and stores it in a cloud warehouse like BigQuery for analysis.

---

## 2. Data Sources and Transformation

Data can originate from:
- APIs (e.g., REST APIs returning JSON)
- RDBMS (e.g., MySQL, PostgreSQL)
- IoT devices
- Web server logs
- Machine-generated data

Transformation tasks include:
- Standardizing date formats (e.g., `YYYY-MM-DD` to `MM-DD-YYYY`)
- Removing null or duplicate records
- Merging columns (e.g., first name + last name)
- Adding calculated fields (e.g., total = price × quantity)

---

## 3. Data Modeling

Data modeling defines how data is structured and related.

- In **relational databases**, data is stored in normalized tables with keys and relationships.
- In **NoSQL**, data is stored in formats like:
  - Key-Value (e.g., Redis)
  - Columnar (e.g., Cassandra)
  - Document (e.g., MongoDB)
  - Graph (e.g., Neo4j)

> Example: In a retail system, you might have a `Customers` table and a `Transactions` table connected via `CustomerID`.

---

## 4. OLTP vs OLAP

- **OLTP (Online Transactional Processing)**:
  - Handles day-to-day transactions
  - Fast inserts, updates, and deletes
  - Row-based storage
  - Example: Banking systems

- **OLAP (Online Analytical Processing)**:
  - Supports complex queries over large datasets
  - Used for historical data analysis
  - Columnar storage
  - Example: Sales trends over the last 5 years

> OLTP is suitable for real-time updates; OLAP is optimized for read-heavy analytics.

---

## 5. Components of Data Architecture

A typical data architecture includes:

- Storage (e.g., databases, lakes, warehouses)
- Data Flow (from source to destination)
- Staging Area (temporary storage for raw data)
- Transformation Layer (ETL/ELT processes)
- Data Warehouse (structured, analytical data storage)
- Interfaces (for external systems to interact)
- Reporting Layer (BI tools like Power BI, Tableau)

> Architecture should align with business goals before deciding on technologies.

---

## 6. Dimensional Modeling

Used in data warehousing to support analytical queries.

- **Fact Tables** contain measurable data (e.g., sales amount, units sold)
- **Dimension Tables** contain descriptive data (e.g., product category, region)

> Example: A `Sales` fact table may link to `Customer`, `Product`, and `Date` dimension tables.

---

## 7. Slowly Changing Dimensions (SCD)

Used when dimension data (like customer address) changes over time.

- **Type 1**: Overwrites old data (no history kept)  
  *Example:* Updating address directly.

- **Type 2**: Adds new rows to maintain full history  
  *Techniques:* 
  - Add `is_active` flag
  - Versioning (v1, v2)
  - Date ranges (`start_date`, `end_date`)

- **Type 3**: Keeps only the previous value  
  *Example:* Columns for `current_city`, `previous_city`

- **Type 6**: Combines Types 1, 2, and 3

---

## 8. Data Marts

A data mart is a subset of a data warehouse, focused on a specific department or use case.

> Example: The marketing team might have a data mart containing campaign performance, customer leads, and conversions.

---

## 9. Data Lakes

Data lakes store raw, unstructured, or semi-structured data.

- Follow **schema-on-read**: the schema is applied only when the data is read.
- Useful for big data scenarios, especially when structure is unknown at ingestion.

> Example: Log files from an application dumped into Amazon S3, later processed using Spark.


