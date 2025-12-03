# ⚡ SQL Optimization Showcase

## Scenario 1: Querying Customer Purchase History
**The Problem:** As the transaction table grew to millions of rows, retrieving a specific customer's history became slow due to a **Full Table Scan**. The database engine was reading every single row to find the matches.

### 1. Original Query (Before Optimization)
This query took **~150ms** to execute on the test dataset.

```sql
EXPLAIN ANALYZE
SELECT * FROM Venta 
WHERE id_cliente = 145 
AND fecha_venta BETWEEN '2024-01-01' AND '2024-12-31';
```

Analysis of Execution Plan:

   - Filter: ((id_cliente = 145) AND (fecha_venta >= ...))
   - Rows Removed by Filter: 1,000,000+
   - Type: Seq Scan on venta (Full Table Scan)

### 2. The Solution: Strategic Indexing
We identified that id_cliente (cardinality: medium) and fecha_venta (cardinality: high) are the primary filtering columns. A Composite B-Tree Index was chosen to cover both predicates efficiently.

```sql
Creating a composite index on client and date
CREATE INDEX idx_venta_cliente_fecha 
ON Venta (id_cliente, fecha_venta);
```

### 3. The Optimized Query (After)
After applying the index, the same query was executed again to verify performance gains.

```sql
EXPLAIN ANALYZE
SELECT * FROM Venta 
WHERE id_cliente = 145 
AND fecha_venta BETWEEN '2024-01-01' AND '2024-12-31';
```

## 🚀 Results
The database engine switched from a Sequential Scan to an Index Scan, jumping directly to the relevant disk pages.

   - Execution Time: Reduced to ~2ms.
   - Improvement: 98% reduction in query latency.
   - Impact: The Customer History dashboard now loads instantly, even under high concurrency


