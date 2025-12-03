# ⚡Unit 1: SQL Optimization & Performance Tuning

## 📌 Overview
In this module, we analyzed the performance of the transactional PostgreSQL database (OLTP) for the Walgreens POS system. As transaction volume increased, query latency degraded significantly.

**Objective:** Reduce query execution time for critical operations (Client History Lookup and Daily Sales Reports).

## 🛠️ Key Techniques Applied
* **Execution Plan Analysis:** Used `EXPLAIN ANALYZE` to identify bottlenecks (Sequential Scans).
* **Indexing Strategy:** Implemented B-Tree indexes on high-cardinality columns (`fecha_venta`, `id_cliente`).
* **Data Typing:** Optimized column data types to reduce storage footprint.

## 📄 Files in this Folder
* `optimization_showcase.md`: Contains the "Before & After" queries and the index creation commands.
* `performance_report.md`: Summary of the query cost reduction (Cost units drop).

---
*Return to [Main Portfolio](../README.md)*
