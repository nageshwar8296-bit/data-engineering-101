# My Understanding of How Data Flows

> This is a personal reference guide I created while learning about data engineering concepts, tools, and architectures. It reflects my understanding of how modern data pipelines work and how different companies approach data infrastructure based on their size and needs.
>
> **If you find any mistakes or have suggestions, please feel free to open an issue or submit a PR — I'm always learning!**

---

### View Interactive Version

For a better viewing experience with interactive features and multiple color themes:

**[View the Interactive Guide](https://nageshwar8296-bit.github.io/data-engineering-101/)**

Features:
- Expandable sections with smooth animations
- Tab navigation (Tool Ecosystem / Company Examples)
- 8 color themes — click the circle in the top-right corner to cycle through them
- Mobile responsive design

---

**What's inside:** A comprehensive overview of the data engineering ecosystem — from data sources to visualization — along with real-world examples of how startups, mid-size companies, and enterprises build their data stacks.

> Click on each section to expand. **Bold** tools are the most popular ones.

---

## Tool Ecosystem

<details>
<summary><b>1. Data Sources</b></summary>

This is where all your data lives originally — your apps, websites, sensors, and files. Think of these as the "raw ingredients" before cooking.

<details>
<summary>Transactional Databases (OLTP)</summary>

Databases that store day-to-day business data — every order, user signup, or payment.

| Tool | Description |
|------|-------------|
| MySQL | Open source, widely used |
| PostgreSQL | Open source, feature-rich |
| SQL Server | Microsoft's database |
| Oracle | Enterprise standard |
| MongoDB | NoSQL document database |

> 💡 *Like a cash register that records every sale as it happens.*

</details>

<details>
<summary>Enterprise Applications</summary>

Big software systems that large companies use to run their entire business.

| Tool | Description |
|------|-------------|
| SAP | Manages everything: inventory, HR, finance, manufacturing |
| Oracle ERP | Similar to SAP, handles company operations |
| Salesforce | Tracks customers, sales, and deals |

> 💡 *Like the brain of a company — knows about employees, products, customers, and money.*

</details>

<details>
<summary>SaaS Applications</summary>

Online tools that companies subscribe to for specific tasks.

| Tool | Description |
|------|-------------|
| HubSpot | Marketing emails, lead tracking |
| Stripe | Online payments |
| Shopify | Online store platform |
| Zendesk | Customer support tickets |

</details>

<details>
<summary>Files & Logs</summary>

Plain files sitting on computers or shared drives.

| Type | Description |
|------|-------------|
| CSV/Excel | Spreadsheet data |
| JSON/XML | Structured text files used by apps |
| Server Logs | Records of what happened on a website or app |

</details>

<details>
<summary>APIs</summary>

Ways for apps to share data with each other automatically.

- REST APIs
- Webhooks
- GraphQL

> 💡 *Like a waiter taking orders between the kitchen (data) and customers (apps).*

</details>

<details>
<summary>Events & Clickstream</summary>

Tracks what users do on websites and apps — every click, scroll, and button press.

- Segment
- Mixpanel
- Google Analytics

> 💡 *Like security cameras recording every movement of shoppers in a store.*

</details>

<details>
<summary>IoT & Sensors</summary>

Data from physical devices — machines, vehicles, wearables.

- Machine Sensors
- GPS Data
- Smart Devices

> 💡 *Like a fitness watch tracking your heartbeat and steps.*

</details>

</details>

---

<details>
<summary><b>2. Data Ingestion</b></summary>

Moving data from sources into a central place. Like collecting ingredients from different shops and bringing them to your kitchen.

<details>
<summary>Batch Ingestion (EL in ELT)</summary>

Copies data in chunks at scheduled times — every hour, daily, etc.

| Tool | Description |
|------|-------------|
| **Fivetran** | Paid, very easy, 300+ connectors ready to use |
| **Airbyte** | Free/open source alternative to Fivetran |
| Stitch | Simpler, good for small teams |
| Hevo | Popular in India, no coding needed |

> 💡 *Like a delivery truck that picks up goods from suppliers every morning.*

</details>

<details>
<summary>Streaming Ingestion</summary>

Moves data instantly as it happens — no waiting.

| Tool | Description |
|------|-------------|
| **Apache Kafka** | Open source, industry standard for streaming |
| **Confluent** | Kafka but managed (easier to use) |
| AWS Kinesis | AWS's streaming service |
| Azure Event Hubs | Azure's streaming service |

> 💡 *Like a live TV broadcast — data flows continuously in real-time.*

</details>

<details>
<summary>Change Data Capture (CDC)</summary>

Only captures what changed — new, updated, or deleted records. Efficient for large databases.

| Tool | Description |
|------|-------------|
| Debezium | Open source CDC |
| Fivetran CDC | Managed CDC service |
| AWS DMS | Database Migration Service |

> 💡 *Like tracking only the edits made to a document, not copying the whole thing every time.*

</details>

</details>

---

<details>
<summary><b>3. Data Storage</b></summary>

Where you keep all your collected data. Like a warehouse or refrigerator where ingredients are stored before cooking.

<details>
<summary>Cloud Object Storage (Data Lakes)</summary>

Cheap storage for massive amounts of raw data — files, images, logs, anything.

| Tool | Description |
|------|-------------|
| AWS S3 | Amazon's storage, most popular |
| Google Cloud Storage | Google's equivalent |
| Azure Blob Storage | Microsoft Azure's storage |

> 💡 *Like a massive storage unit — dump everything here, sort it later.*

</details>

<details>
<summary>File Formats</summary>

How data is packaged and stored. Some formats are faster to read, some save more space.

| Format | Description |
|--------|-------------|
| **Parquet** | Most popular for analytics, compressed, fast |
| Avro | Good for streaming data |
| ORC | Optimized for Hive |
| Delta | Modern format with database-like features |
| Iceberg | Modern format with database-like features |

> 💡 *Like choosing between a ZIP file or a folder — same content, different packaging.*

</details>

<details>
<summary>Data Warehouses</summary>

Organized storage built for fast analysis. Data is cleaned and structured here.

| Tool | Description |
|------|-------------|
| Redshift | Amazon's warehouse |
| BigQuery | Google's warehouse |
| Synapse | Microsoft's warehouse |
| **Snowflake** | Works on any cloud, very popular |
| **Databricks** | Lakehouse (warehouse + lake combined) |

> 💡 *Like an organized library — books are sorted and easy to find quickly.*

</details>

</details>

---

<details>
<summary><b>4. Data Transformation</b></summary>

Cleaning and reshaping raw data into useful formats. Like cooking raw ingredients into a proper meal.

<details>
<summary>ELT (Modern - in-warehouse)</summary>

Transform data inside the warehouse using SQL. The modern, preferred approach.

| Tool | Description |
|------|-------------|
| **dbt** | Industry standard, works everywhere, free |
| Dataform | Google's tool, built into BigQuery |
| Coalesce | Visual tool for Snowflake |
| SQLMesh | Newer alternative to dbt |

> 💡 *Like cooking inside the restaurant kitchen (warehouse) itself.*

</details>

<details>
<summary>ETL (Traditional - outside warehouse)</summary>

Transform data before loading into warehouse. Older approach, still used in big companies.

| Tool | Description |
|------|-------------|
| Informatica | Enterprise giant, expensive but powerful |
| Talend | Has free open-source version |
| SSIS | Microsoft's tool for SQL Server |
| DataStage | IBM's enterprise tool |
| Pentaho | Open source ETL |

> 💡 *Like preparing food at a central kitchen, then delivering to restaurants.*

</details>

<details>
<summary>Streaming Transformation</summary>

Transform data as it flows in real-time — no waiting for batches.

| Tool | Description |
|------|-------------|
| **Apache Flink** | Powerful real-time processing |
| Spark Streaming | Part of Spark, handles batch + stream |
| ksqlDB | SQL on top of Kafka streams |

> 💡 *Like a sushi chef preparing food as customers order — instant.*

</details>

</details>

---

<details>
<summary><b>5. Query Engines</b></summary>

Tools that let you run SQL queries directly on data lakes (files) without loading into a warehouse first. Useful for quick exploration.

| Tool | Description |
|------|-------------|
| Presto | Open source, query any data source |
| Trino | Fork of Presto, very active |
| AWS Athena | AWS service, query S3 files with SQL |
| Dremio | Fast queries on data lakes |

> 💡 *Like reading a book in the storage room instead of bringing it to your desk first.*

</details>

---

<details>
<summary><b>6. Orchestration</b></summary>

Scheduling and managing workflows — making sure tasks run in the right order at the right time. The "project manager" of data pipelines.

| Tool | Description |
|------|-------------|
| **Apache Airflow** | Industry standard, open source, most popular |
| Prefect | Modern alternative, easier to use |
| Dagster | Focused on data assets |
| AWS Step Functions | AWS's workflow service |
| Azure Data Factory | Azure's orchestration |
| Cloud Composer | Google's managed Airflow |

> 💡 *Like an alarm clock + calendar that automatically triggers tasks: "At 6 AM, run pipeline A, then B, then C."*

</details>

---

<details>
<summary><b>7. Data Quality & Testing</b></summary>

Checking if data is correct, complete, and trustworthy. Catches problems before they reach dashboards and reports.

| Tool | Description |
|------|-------------|
| **Great Expectations** | Open source, write rules for data validation |
| dbt tests | Built into dbt, simple checks |
| Soda | Easy data monitoring |
| Monte Carlo | Detects data issues automatically |
| Bigeye | Data observability platform |

> 💡 *Like quality control in a factory — checking products before shipping them out.*

</details>

---

<details>
<summary><b>8. Data Catalog & Governance</b></summary>

Helps people find and understand data. "What tables exist? What does this column mean? Who owns this data?"

<details>
<summary>Open Source</summary>

| Tool | Description |
|------|-------------|
| DataHub | LinkedIn's tool, very popular |
| Amundsen | Built by Lyft |
| Apache Atlas | Apache's governance tool |

</details>

<details>
<summary>Commercial</summary>

| Tool | Description |
|------|-------------|
| Alation | Enterprise catalog, AI-powered |
| Collibra | Big on governance and compliance |
| Atlan | Modern, collaborative workspace |

</details>

> 💡 *Like a library catalog — tells you what books exist, where to find them, and what they're about.*

</details>

---

<details>
<summary><b>9. BI & Visualization</b></summary>

Tools that turn data into charts, dashboards, and reports. This is what business users actually see and use.

<details>
<summary>Enterprise</summary>

Powerful tools used by large companies. Usually expensive.

| Tool | Description |
|------|-------------|
| **Tableau** | Beautiful visuals, drag-and-drop, owned by Salesforce |
| **Power BI** | Microsoft's tool, great with Excel |
| Looker | Google's BI tool, code-based modeling |

</details>

<details>
<summary>Open Source / Lightweight</summary>

Free or cheap alternatives. Good for startups and small teams.

| Tool | Description |
|------|-------------|
| Metabase | Super easy, no SQL needed |
| Apache Superset | Airbnb's tool, powerful and free |
| Redash | Simple SQL-based dashboards |

</details>

> 💡 *Like the final dish presentation — making data look appetizing for business people.*

</details>

---

<details>
<summary><b>10. DevOps & Infrastructure</b></summary>

Tools that help deploy, manage, and version your code and infrastructure. The foundation that keeps everything running.

<details>
<summary>Containerization</summary>

Package your code with everything it needs to run anywhere.

| Tool | Description |
|------|-------------|
| **Docker** | Creates containers (portable app packages) |
| **Kubernetes** | Manages many containers at scale |

> 💡 *Like shipping containers — your stuff stays safe and works the same everywhere.*

</details>

<details>
<summary>Version Control</summary>

Track changes to code. Collaborate without overwriting each other's work.

| Tool | Description |
|------|-------------|
| **Git** | The system that tracks changes |
| GitHub | Website to store and share Git code |
| GitLab | Alternative to GitHub with more built-in tools |

> 💡 *Like "Track Changes" in Word, but for code — see who changed what and when.*

</details>

<details>
<summary>Infrastructure as Code</summary>

Define your servers, databases, and cloud resources in code files instead of clicking buttons.

| Tool | Description |
|------|-------------|
| Terraform | Most popular, works with all clouds |
| Pulumi | Use real programming languages |

> 💡 *Like a blueprint for a building — anyone can recreate the same setup from the plan.*

</details>

</details>

---

## Company Examples

See how different companies build their data pipelines based on their size and needs.

<details>
<summary><b>🚀 Small Company / Startup</b> (5-50 employees)</summary>

**Philosophy:** Keep it simple. Use managed services to avoid hiring a big data team. Focus on getting insights quickly rather than building complex infrastructure.

### Pipeline Flow

```
Sources (Shopify, Stripe) → Ingestion (Fivetran) → Warehouse (BigQuery) → Transform (dbt) → BI (Metabase)
```

### Example: Online T-Shirt Store

A small e-commerce startup sells t-shirts via Shopify. They use **Fivetran** to automatically pull Shopify orders and Stripe payments into **BigQuery** every hour. A single data analyst uses **dbt** to create clean tables for revenue, customers, and inventory. The CEO views a **Metabase** dashboard each morning showing yesterday's sales.

### Full Stack

| Step | Tool |
|------|------|
| 1. Data Sources | Shopify, Stripe, PostgreSQL |
| 2. Extract & Load | Fivetran or Airbyte |
| 3. Warehouse | BigQuery or Snowflake |
| 4. Transform | dbt (free) |
| 5. Visualization | Metabase (free) |

</details>

<details>
<summary><b>🏢 Mid-Size Company</b> (50-500 employees)</summary>

**Philosophy:** Balance between simplicity and robustness. Add orchestration to manage multiple pipelines. Start monitoring data quality. Need proper scheduling and alerts.

### Pipeline Flow

```
Sources (Salesforce, MySQL) → Ingestion (Fivetran + Kafka) → Storage (S3 + Snowflake) → Transform (dbt + Airflow) → Quality (Great Expectations) → BI (Tableau)
```

### Example: B2B SaaS Company

A SaaS company with 200 employees tracks customers in **Salesforce**, marketing in **HubSpot**, and product usage in their own **MySQL** database. **Fivetran** syncs these to **Snowflake**. Real-time product events flow through **Kafka**. **Airflow** runs dbt models every morning at 6 AM. **Great Expectations** checks if revenue numbers look correct. Sales team uses **Tableau** dashboards to track pipeline and churn.

### Full Stack

| Step | Tool |
|------|------|
| 1. Data Sources | Salesforce, HubSpot, MySQL |
| 2. Batch Ingestion | Fivetran |
| 3. Streaming | Apache Kafka |
| 4. Data Lake | AWS S3 (Parquet) |
| 5. Warehouse | Snowflake |
| 6. Orchestration | Apache Airflow |
| 7. Transform | dbt |
| 8. Data Quality | Great Expectations |
| 9. Visualization | Tableau / Power BI |

</details>

<details>
<summary><b>🏛️ Large Enterprise</b> (500+ employees)</summary>

**Philosophy:** Enterprise-grade reliability, security, and governance. Multiple pipelines for different use cases. Legacy systems mixed with modern tools. Need data catalog so people can find data. Compliance and audit trails are critical.

### Pipeline Flow

```
Sources (SAP, Oracle, IoT) → CDC (Debezium) → Streaming (Confluent) → Lake (S3 + Delta) → Lakehouse (Databricks) → Transform (dbt + Informatica) → Catalog (DataHub) → BI (Multiple)
```

### Example: Global Manufacturing Company

A manufacturing giant with 10,000 employees runs **SAP** for inventory and finance, **Salesforce** for sales, and collects **IoT sensor data** from factory machines. **Debezium** captures every database change in real-time. **Confluent Kafka** streams millions of events per second. Raw data lands in **S3** as Delta Lake tables. **Databricks** processes both batch and streaming data. Legacy **Informatica** jobs still run alongside modern **dbt** models. **DataHub** catalogs 5,000+ tables so analysts can find what they need. Finance uses **Power BI**, sales uses **Tableau**, and executives use **Looker** dashboards.

### Full Stack

| Step | Tool |
|------|------|
| 1. Enterprise Sources | SAP, Oracle ERP, Salesforce |
| 2. Real-time Sources | IoT Sensors, APIs, Logs |
| 3. CDC | Debezium |
| 4. Streaming | Confluent Kafka |
| 5. Data Lake | S3 + Delta Lake |
| 6. Lakehouse | Databricks |
| 7. Orchestration | Airflow + Dagster |
| 8. Modern Transform | dbt |
| 9. Legacy Transform | Informatica |
| 10. Data Quality | Monte Carlo |
| 11. Data Catalog | DataHub / Alation |
| 12. BI Tools | Tableau, Power BI, Looker |

</details>

---

## Quick Comparison

| Aspect | 🚀 Small | 🏢 Mid-Size | 🏛️ Enterprise |
|--------|----------|-------------|---------------|
| **Team Size** | 1-2 data people | 5-15 data team | 50+ across teams |
| **Data Volume** | GBs | TBs | PBs (Petabytes) |
| **Budget** | $500-5K/month | $10K-100K/month | $500K+/month |
| **Orchestration** | Manual / cron | Airflow / Prefect | Multiple orchestrators |
| **Streaming** | Usually not needed | Some use cases | Critical for real-time |
| **Data Catalog** | Spreadsheet / Notion | Basic catalog | Enterprise catalog |
| **Governance** | Minimal | Basic access controls | Full compliance |
| **Transform** | dbt only | dbt + Python | dbt + Legacy ETL + Spark |

---

## Contributing

Feel free to submit issues and pull requests to improve this guide!

## License

MIT License
