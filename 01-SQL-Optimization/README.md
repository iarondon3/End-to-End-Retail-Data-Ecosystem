# ⚡ Unit 1: SQL Optimization & Performance Tuning

## 📌 Overview
In this module, we analyze and resolve performance bottlenecks in the transactional PostgreSQL database (OLTP).
We simulate a real-world analytical scenario where the lack of proper indexing degrades system performance.

**Objective:** Reduce query execution time (Cost) for heavy reporting queries involving multiple table joins.

## 🛠️ Key Techniques Applied
* **Execution Plan Analysis:** Used `EXPLAIN ANALYZE` to identify bottlenecks (Sequential Scans and Hash Joins on large tables).
* **Indexing Strategy:** Implemented B-Tree indexes to target specific bottlenecks:
* **Interactive Simulation:** Created a reproducible environment where users can stress-test the database with variable volumes (up to 500k records) to visualize the optimization impact.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1f_EAGTVF8MTHsQNBM_mxVcyChgx9OyOd#scrollTo=zzGvzOPERk1F)

## 📄 Files in this Folder
* **[`optimization_demo.ipynb`](./optimization_demo.ipynb)**: 🌟 ***Interactive Demo.*** A Colab Notebook where you can generate the data, run the complex slow queries, apply the indexes, and verify the performance boost yourself. **(Click the "Open in Colab" badge above to run it).**
* **[`optimization_showcase.md`](./optimization_showcase.md)**: A static narrative of the problem and solution (Code & Explanation).

---
*Return to [Main Portfolio](../README.md)*
