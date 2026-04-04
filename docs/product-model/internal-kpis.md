# Internal KPIs

Internal KPIs are operational indicators that measure the performance and health of individual data products. They sit below Outcome KPIs in the measurement hierarchy and provide the product-level evidence that supports business-level outcomes.

---

## What Internal KPIs Are

An Internal KPI is a measurable indicator owned by a data product. It tracks operational aspects such as availability, freshness, error rates, usage patterns, and delivery speed.

Internal KPIs are owned by the **Product Manager** or **Product Owner**. They answer: "Is this product performing as expected?"

---

## KPI Structure

Internal KPIs share the same structure as Outcome KPIs:

| Field | Description |
|---|---|
| `name` | Short, descriptive name |
| `description` | What this KPI measures |
| `type` | Category (e.g. `internal`, `operational`, `technical`) |
| `unit` | Unit of measurement |
| `targetValue` | The target to achieve |
| `currentValue` | Latest measured value |
| `valueSource` | How the current value is obtained (`manual`, `system`, `query`, `api`) |
| `dataProductId` | The product this KPI belongs to |
| `parentKpiId` | Optional link to a parent KPI (for hierarchies) |
| `version` | Semantic version |
| `lifecycle` | Current lifecycle state |

---

## Parent-Child Hierarchies

Internal KPIs support parent-child relationships through the `parentKpiId` field. This enables KPI hierarchies:

- A top-level KPI "Data Freshness" can have child KPIs for each source table.
- A "Quality Score" KPI can aggregate child KPIs for individual dimensions.

Hierarchies make it possible to drill from a summary metric to the contributing components.

---

## Linking to Products

Every Internal KPI is linked to a data product through the `dataProductId` field. A product can have many Internal KPIs, but each KPI belongs to exactly one product.

Products can also be linked to Outcome KPIs through explicit link records that capture the relationship type (e.g. `supports`, `contributes_to`). This creates the full traceability chain:

**Objective** → **Outcome KPI** → **Data Product** → **Internal KPI**

---

## Common Internal KPIs

| KPI | Unit | Description |
|---|---|---|
| API Availability | % | Percentage of time the product API is responsive |
| Data Freshness | minutes | Time since the last data update |
| Error Rate | % | Percentage of failed requests or operations |
| Query Latency (p95) | ms | 95th percentile query response time |
| Row Count | count | Total rows in the product dataset |
| Consumer Count | count | Number of active consumers |
| DQ Score | 0-100 | Overall data quality score from DQ checks |

---

## Value Sources

Like Outcome KPIs, Internal KPIs support four value sources:

| Source | Description |
|---|---|
| **Manual** | Value entered by a human |
| **System** | Value computed by the platform |
| **Query** | Value from a database query |
| **API** | Value from an external API |

For Internal KPIs, `system` and `query` sources are more common since operational metrics are often directly observable.

---

## What Internal KPIs Do Not Do

- **Do not measure business outcomes.** Use Outcome KPIs for that.
- **Do not replace monitoring.** KPIs capture point-in-time values; monitoring provides continuous observability.
- **Do not aggregate across products.** Each Internal KPI belongs to one product. Cross-product views are provided by the dashboard.
