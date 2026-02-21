# Outcome KPIs

Outcome KPIs measure whether business objectives are being achieved. They are the evidence layer between strategic intent and operational execution.

---

## What Outcome KPIs Are

An Outcome KPI is a measurable indicator that tracks progress toward a business objective. It answers the question: "How do we know this objective is succeeding?"

Outcome KPIs are owned by the **Outcome Owner** and linked to objectives. They measure business impact — not product performance. A good Outcome KPI reflects a change in the world (revenue growth, risk reduction, customer satisfaction), not a change in the system (API calls, row counts, uptime).

---

## KPI Structure

| Field | Description |
|---|---|
| `name` | Short, descriptive name |
| `description` | What this KPI measures and why it matters |
| `type` | Category of the KPI (e.g. `outcome`, `business`, `strategic`) |
| `unit` | Unit of measurement (e.g. `%`, `USD`, `count`, `days`) |
| `targetValue` | The target to achieve |
| `currentValue` | Latest measured value |
| `valueSource` | How the current value is obtained |
| `version` | Semantic version |
| `lifecycle` | Current lifecycle state |

---

## Value Sources

Outcome KPIs support four value sources:

| Source | Description |
|---|---|
| **Manual** | Value entered by a human. Suitable for strategic metrics updated quarterly. |
| **System** | Value computed by the platform from internal data. |
| **Query** | Value obtained by executing a database query. |
| **API** | Value fetched from an external system via API call. |

The value source determines how the `currentValue` is populated. Manual is the default and most common for Outcome KPIs, since they often measure business outcomes that are not directly observable by the platform.

---

## Linking to Objectives

Outcome KPIs are linked to objectives through a structured relationship. Each objective can have multiple KPIs, and each KPI can potentially serve multiple objectives.

The link creates a traceable chain:

**Objective** → "Increase customer retention by 15%"
**Outcome KPI** → "Customer retention rate" (target: 85%, current: 78%)

This chain makes it visible whether strategic goals have measurable indicators and whether those indicators are being tracked.

---

## Outcome KPIs vs Internal KPIs

| Aspect | Outcome KPI | Internal KPI |
|---|---|---|
| **Owned by** | Outcome Owner | Product Manager / Product Owner |
| **Measures** | Business impact | Product performance |
| **Linked to** | Objectives | Data Products |
| **Examples** | Revenue growth, customer satisfaction, compliance rate | API latency, data freshness, error rate |
| **Visibility** | Enterprise / domain level | Product level |

Outcome KPIs answer "Is the business succeeding?" Internal KPIs answer "Is the product performing?"

---

## What Outcome KPIs Do Not Do

- **Do not measure product performance.** Use Internal KPIs for that.
- **Do not auto-update from product metrics.** Business outcomes require deliberate measurement.
- **Do not replace business reporting.** They are governance artifacts, not BI dashboards.
- **Do not cascade automatically.** Changes to an objective do not automatically adjust KPI targets.
