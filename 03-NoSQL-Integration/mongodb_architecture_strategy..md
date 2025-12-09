# 🍃 MongoDB Architecture & Integration Strategy

## 1. Architectural Justification: Why MongoDB?
To complement the robust transactional architecture (PostgreSQL) of the Walgreens Point of Sale system, **MongoDB** was selected to handle new use cases focused on **Consumer Behavior Analysis**.

The decision to choose a **Document-Oriented Database** over other NoSQL alternatives was driven by specific technical requirements:

* **vs. Key-Value (Redis):** While Redis is ultra-fast, it lacks the expressive query power needed for complex aggregations (e.g., calculating average basket size per customer segment).
* **vs. Graph (Neo4j):** Graph databases excel at traversing relationships. However, our analytical focus is on **event aggregation** (sales volumes, channel segmentation) rather than exploring deep network connections.

---

## 2. Data Modeling Pattern: Pure Embedding
We adopted a **Denormalized "Pure Embedding" Strategy**. Instead of maintaining normalized references (Foreign Keys) requiring expensive JOINs, we embed all context directly into the main document.

### 📂 [View Sample JSON Document](./sales_collection_sample.json)

**The Strategy:**
* **Embedding vs. Referencing:** We embedded `Customer`, `Branch`, and `Items` directly inside the `Sale` document.
* **Why?** This aligns with the **"Data Locality"** principle. A single `find()` operation retrieves the complete history of a transaction without needing to "stitch" data from 4 different tables. It optimizes read performance for dashboards that need to show "What, Who, and Where" instantly.

---

## 3. Reliability & CAP Theorem
Reliability is non-negotiable for retail operations. In the context of the **CAP Theorem** (Brewer's Theorem), MongoDB is configured as a **CP System (Consistency & Partition Tolerance)**.

* **Implication:** In the event of a network partition, the system prioritizes **Data Consistency** over Availability.
* **Business Impact:** This ensures that analytical reports regarding revenue are always accurate. The system prevents conflicting or stale data, ensuring the "Single Source of Truth" remains uncorrupted for decision-making.

---

## 4. Analytical Power: The Aggregation Pipeline
The primary driver for this integration is MongoDB's **Aggregation Framework**, which allows us to process data server-side without extracting it to an external ETL tool.

**Key Metrics Computed:**
1.  **Sales by Channel:** Comparing `STORE` vs. `ONLINE` performance.
2.  **Geographic Analysis:** Total revenue aggregation by `branch.country`.
3.  **Basket Analysis:** Calculating the **Average Basket Size** per Customer using `$unwind` and `$group` stages on the embedded `items` array.
