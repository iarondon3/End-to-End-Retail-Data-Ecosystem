# 🏗️ Stage 0: Environment Setup & Data Generation

## 📌 Overview
Before analyzing data, we need to create it. This module contains the reproducible pipeline used to generate the synthetic datasets for the Walgreens POS system.

**Objective:** Provide a self-contained script that allows any engineer to replicate the database schema and populate it with realistic synthetic data using Python.

## ⚙️ Interactive Configuration
**Customize your scenario:**

The data generation pipeline is fully parametric. Inside the Notebook, you will find a configuration cell where you can adjust the volume of the dataset to simulate different operational scales:

* **Demo Mode:** Keep default values (`sales: 5000`) for a quick execution.
* **Stress Test:** Increase `sales` to `100,000` or more to test the database performance and query optimization strategies under heavy load.

## 🛠️ Tools Used
* **Python:** Core scripting logic.
* **Faker:** Library for generating realistic dummy data (names, addresses, dates).
* **Psycopg2:** High-performance PostgreSQL adapter used for efficient data insertion.

## 🚀 How to Run
You can simulate the data generation process directly in your browser without installing any local dependencies. Click the badge below to open the interactive environment:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1d5HqYy7v3fKrU-zRBrxEW8AnAtk_gic8#scrollTo=ANvhAiRSrtWT)

## 📄 Files in this Folder
* **[`data_generation_pipeline.ipynb`](./data_generation_pipeline.ipynb)**: The interactive Colab Notebook containing the DDL schemas and the Python generation script. **Use this to customize the data volume.**
* **[`schema_definition.sql`](./schema_definition.sql)**: Raw SQL file for table creation (PostgreSQL).

---
*Return to [Main Portfolio](../README.md)*
