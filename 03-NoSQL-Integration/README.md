
# 🍃 Unit 3: NoSQL Integration & Consumer Analytics


## 📌 Overview
In this module, we extend the data platform by integrating **MongoDB (NoSQL)** to handle "Read-Heavy" analytical workloads. While PostgreSQL handles transactional integrity, MongoDB is utilized to analyze complex consumer behavior patterns that require flexible schemas and fast retrieval of hierarchical data.

**Objective:** Design and execute an **ETL Pipeline** to transform rigid SQL tables into rich, nested JSON documents, optimized for high-performance dashboards.

## 🛠️ Key Techniques Applied
* **ETL Pipeline (SQL to NoSQL):** Built a Python-based migration script that extracts relational data, performs in-memory "joins", and constructs denormalized documents.
* **Data Modeling (Pure Embedding):** Implemented a **Denormalized Strategy** by embedding `Customer`, `Branch`, and `Items` directly into the `Sale` document. This eliminates the need for expensive JOINs during read operations.
* **Advanced Analytics:** Leveraged the **MongoDB Aggregation Framework** (`$unwind`, `$group`, `$addFields`) to calculate complex metrics like "Average Basket Size per Customer".

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1tlTGU8N8uUloPpfxdKSdtA7okvKdAdHh#scrollTo=jZ4IsyIFR10H)

## 📄 Files in this Folder
* **[`migration_lab.ipynb`](./migration_lab.ipynb)**: 🌟 **Interactive Migration Lab.** A Colab Notebook where you can simulate the full pipeline: Generating raw SQL-like data, running the Python ETL transformation, and executing Aggregation queries on an in-memory MongoDB instance. **(Click the Badge above to run).**
* **[`mongodb_architecture_strategy.md`](./mongodb_architecture_strategy.md)**: A technical decision record (ADR) explaining the choice of MongoDB over Redis/Neo4j, the justification for the "Pure Embedding" pattern, and CAP Theorem considerations.
* **[`sales_collection_sample.json`](./sales_collection_sample.json)**: A sample JSON document demonstrating the final schema structure, showing how customer and product details are embedded within the transaction.

---
*Return to [Main Portfolio](../README.md)*
