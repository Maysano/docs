# REST API

Maysano exposes a RESTful JSON API at the `/api/*` route prefix. All endpoints require authentication unless otherwise noted.

---

## Data Products

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/products` | List all data products |
| `GET` | `/api/products/:id` | Get a data product by ID |
| `POST` | `/api/products` | Create a new data product |
| `PATCH` | `/api/products/:id` | Update a data product |
| `DELETE` | `/api/products/:id` | Delete a data product |
| `GET` | `/api/products/:id/versions` | List versions for a product |
| `POST` | `/api/products/:id/versions` | Publish a new version |
| `GET` | `/api/products/:id/versions/:versionId` | Get a specific version |
| `GET` | `/api/products/:id/content-fields` | List content schema fields |
| `POST` | `/api/products/:id/content-fields` | Add a content schema field |
| `PATCH` | `/api/products/:id/content-fields/:fieldId` | Update a content field |
| `DELETE` | `/api/products/:id/content-fields/:fieldId` | Delete a content field |
| `GET` | `/api/products/:id/activities` | List product activities |

---

## Objectives

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/objectives` | List all business objectives |
| `GET` | `/api/objectives/:id` | Get an objective with linked KPIs, products, and use cases |
| `POST` | `/api/objectives` | Create a new objective |
| `PATCH` | `/api/objectives/:id` | Update an objective |
| `DELETE` | `/api/objectives/:id` | Delete an objective |
| `GET` | `/api/objectives/:id/history` | Get change history for an objective |
| `POST` | `/api/objectives/:id/kpis` | Link a KPI to an objective |
| `DELETE` | `/api/objectives/:id/kpis/:kpiId` | Unlink a KPI from an objective |
| `POST` | `/api/objectives/:id/products` | Link a product to an objective |
| `DELETE` | `/api/objectives/:id/products/:productId` | Unlink a product from an objective |
| `POST` | `/api/objectives/:id/use-cases` | Link a use case to an objective |
| `DELETE` | `/api/objectives/:id/use-cases/:useCaseId` | Unlink a use case from an objective |

---

## KPIs

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/kpis` | List all KPIs (filterable by type, product) |
| `GET` | `/api/kpis/:id` | Get a KPI by ID |
| `POST` | `/api/kpis` | Create a new KPI |
| `PATCH` | `/api/kpis/:id` | Update a KPI |
| `DELETE` | `/api/kpis/:id` | Delete a KPI |
| `GET` | `/api/products/:id/kpi-links` | List KPI links for a product |
| `POST` | `/api/products/:id/kpi-links` | Link a KPI to a product |
| `DELETE` | `/api/products/:id/kpi-links/:linkId` | Unlink a KPI from a product |

---

## Governance Profiles

### DQ Profiles

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/data-quality-profiles` | List all DQ profiles |
| `GET` | `/api/data-quality-profiles/:id` | Get a DQ profile by ID |
| `POST` | `/api/data-quality-profiles` | Create a DQ profile |
| `PATCH` | `/api/data-quality-profiles/:id` | Update a DQ profile |
| `DELETE` | `/api/data-quality-profiles/:id` | Delete a DQ profile |

### SLA Profiles

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/sla-profiles` | List all SLA profiles |
| `GET` | `/api/sla-profiles/:id` | Get an SLA profile by ID |
| `POST` | `/api/sla-profiles` | Create an SLA profile |
| `PATCH` | `/api/sla-profiles/:id` | Update an SLA profile |
| `DELETE` | `/api/sla-profiles/:id` | Delete an SLA profile |

### Access Profiles

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/access-profiles` | List all access profiles |
| `GET` | `/api/access-profiles/:id` | Get an access profile by ID |
| `POST` | `/api/access-profiles` | Create an access profile |
| `PATCH` | `/api/access-profiles/:id` | Update an access profile |
| `DELETE` | `/api/access-profiles/:id` | Delete an access profile |

### Pricing Plans

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/pricing-plans` | List all pricing plans |
| `GET` | `/api/pricing-plans/:id` | Get a pricing plan by ID |
| `POST` | `/api/pricing-plans` | Create a pricing plan |
| `PATCH` | `/api/pricing-plans/:id` | Update a pricing plan |
| `DELETE` | `/api/pricing-plans/:id` | Delete a pricing plan |

---

## DQ Operations

### Connections

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/dq/connections` | List all DQ connections |
| `GET` | `/api/dq/connections/:id` | Get a connection by ID |
| `POST` | `/api/dq/connections` | Create a new connection |
| `DELETE` | `/api/dq/connections/:id` | Delete a connection |
| `GET` | `/api/dq/connections/:id/schemas` | List schemas for a connection |
| `GET` | `/api/dq/connections/:id/schemas/:schema/tables` | List tables in a schema |
| `GET` | `/api/dq/connections/:id/schemas/:schema/tables/:table/columns` | List columns in a table |
| `POST` | `/api/dq/connections/:id/test` | Test connection health |
| `POST` | `/api/dq/products/:id/setup-connection` | Setup or recover a product connection |

### Checks

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/dq/checks` | List checks (filterable by connection, table) |
| `GET` | `/api/dq/checks/:id` | Get a check by ID |
| `POST` | `/api/dq/checks` | Create a new check |
| `PATCH` | `/api/dq/checks/:id` | Update a check |
| `DELETE` | `/api/dq/checks/:id` | Delete a check |
| `POST` | `/api/dq/checks/:id/run` | Run a single check |
| `POST` | `/api/dq/checks/batch-run` | Run multiple checks |
| `GET` | `/api/dq/check-types` | List available check types |

### Results and Scores

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/dq/checks/:id/results` | Get results for a check |
| `GET` | `/api/dq/products/:id/dimension-scores` | Get dimension scores for a product |
| `GET` | `/api/dq/products/:id/dimension-scores/:dimension` | Get detailed scores for a dimension |

### Incidents

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/dq/incidents` | List incidents (filterable by check, status) |
| `GET` | `/api/dq/incidents/:id` | Get an incident by ID |
| `PATCH` | `/api/dq/incidents/:id` | Update incident (acknowledge, resolve) |

---

## Quality Intelligence

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/quality-intelligence/summary` | Generate executive quality summary |
| `POST` | `/api/quality-intelligence/remediation` | Generate remediation advice for a dimension |
| `POST` | `/api/quality-intelligence/remediation/all` | Generate remediation for all failing checks |
| `POST` | `/api/quality-intelligence/recommend-checks` | Get AI check recommendations for a table |
| `POST` | `/api/quality-intelligence/batch-auto-setup` | Batch auto-setup (SSE stream) |

---

## AI Assistant

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/ai/chat` | Send a message to the AI assistant (streaming) |
| `POST` | `/api/ai/generate-spec` | Generate an ODPS specification |
| `POST` | `/api/ai/validate-spec` | Validate an existing specification |
| `GET` | `/api/ai/conversations` | List conversation sessions |
| `GET` | `/api/ai/conversations/:id` | Get messages for a conversation |

---

## Guidance Rulesets

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/guidance-rules` | List all guidance rules |
| `POST` | `/api/guidance-rules` | Create a guidance rule |
| `PATCH` | `/api/guidance-rules/:id` | Update a guidance rule |
| `DELETE` | `/api/guidance-rules/:id` | Delete a guidance rule |
| `GET` | `/api/guidance-rulesets` | List published rulesets |
| `POST` | `/api/guidance-rulesets/publish` | Publish current rules as a new ruleset |
| `POST` | `/api/guidance-rulesets/:id/activate` | Activate a specific ruleset |

---

## Templates

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/templates` | List all product templates |
| `GET` | `/api/templates/:id` | Get a template by ID |
| `POST` | `/api/templates` | Create a template |
| `PATCH` | `/api/templates/:id` | Update a template |
| `DELETE` | `/api/templates/:id` | Delete a template |

---

## GitHub Integration

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/github/connection` | Get current GitHub connection status |
| `POST` | `/api/github/connect` | Connect a GitHub account |
| `DELETE` | `/api/github/disconnect` | Disconnect GitHub account |
| `GET` | `/api/github/repos` | List accessible repositories |
| `POST` | `/api/github/sync` | Sync a product to a GitHub repository |

---

## Users and Roles

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/users` | List all users (admin only) |
| `GET` | `/api/users/:id` | Get user with roles |
| `PATCH` | `/api/users/:id` | Update user details |
| `POST` | `/api/users/:id/roles` | Assign a role to a user |
| `DELETE` | `/api/users/:id/roles/:roleId` | Remove a role from a user |
| `GET` | `/api/roles` | List all available roles |

---

## Common Patterns

### Request Format

All write operations (`POST`, `PATCH`) expect a JSON body. Request bodies are validated against Zod schemas. Invalid requests return a `400` status with structured error details.

### Response Format

All endpoints return JSON responses. Successful operations return the created or updated resource. List endpoints return arrays.

### Error Responses

| Status | Meaning |
|---|---|
| `400` | Invalid request body or parameters |
| `401` | Not authenticated |
| `403` | Insufficient permissions |
| `404` | Resource not found |
| `500` | Internal server error |

### Pagination

List endpoints for DQ operations support pagination via `offset` and `limit` query parameters. The response includes `total`, `offset`, and `limit` fields.
