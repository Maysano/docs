# Events

Maysano generates events to track changes across the platform. Events provide an immutable, append-only audit trail of what happened, when, and by whom.

---

## Event Types

Maysano produces three categories of events:

### Structural Events

Structural events track portfolio-level changes — the creation, modification, and removal of entities across the system.

| Field | Description |
|---|---|
| `entityType` | What kind of entity changed (e.g. `product`, `objective`, `kpi`, `sla_profile`) |
| `entityId` | ID of the affected entity |
| `entityName` | Name of the affected entity |
| `eventType` | What happened (e.g. `created`, `updated`, `deleted`, `published`, `status_changed`) |
| `metadata` | Additional context (old/new values, related entities) |
| `createdAt` | When the event occurred |

Structural events capture portfolio evolution: new products appearing, components being retired, lifecycle transitions, and relationship changes.

---

### Product Activities

Product activities track changes at the individual product level:

| Field | Description |
|---|---|
| `productId` | The affected product |
| `productName` | Product name at the time of the event |
| `activityType` | What happened (e.g. `created`, `updated`, `version_published`, `governance_attached`) |
| `description` | Human-readable description |
| `details` | Additional context |
| `performedBy` | Who performed the action |
| `createdAt` | When the activity occurred |

Product activities provide a chronological audit trail for each product.

---

### Objective History

Objective history tracks changes to business objectives:

| Field | Description |
|---|---|
| `objectiveId` | The affected objective |
| `action` | What happened (e.g. `created`, `updated`, `status_changed`, `kpi_linked`, `product_linked`) |
| `field` | Which field changed (for updates) |
| `oldValue` | Previous value |
| `newValue` | New value |
| `summary` | Human-readable change summary |
| `performedBy` | Who made the change |
| `createdAt` | When the change occurred |

---

## Event Immutability

All events are append-only. Once recorded, an event cannot be modified or deleted. This ensures:

- **Audit compliance** — the full history of every entity is preserved.
- **Traceability** — any state can be reconstructed by replaying events.
- **Accountability** — every change is attributed to a specific user.

---

## Server-Sent Events (SSE)

For long-running operations, Maysano uses Server-Sent Events to stream real-time progress updates to the client.

### Batch Auto-Setup SSE

The batch auto-setup endpoint (`POST /api/quality-intelligence/batch-auto-setup`) returns an SSE stream with the following event types:

**Recommend Phase:**

| Event | Description |
|---|---|
| `recommend_phase_start` | Phase started, includes total table count |
| `recommend_start` | Processing started for a specific table |
| `recommend_complete` | Recommendations ready for a table |
| `recommend_error` | Recommendation failed for a table |
| `recommend_phase_done` | All tables processed |

**Create and Run Phase:**

| Event | Description |
|---|---|
| `create_phase_start` | Phase started, includes total check count |
| `create_progress` | A check was successfully created |
| `create_error` | Check creation failed |
| `create_phase_done` | All checks processed |
| `run_start` | Batch check execution started |
| `run_complete` | Batch execution finished |

**General:**

| Event | Description |
|---|---|
| `done` | Operation completed successfully |
| `error` | Fatal error occurred |

---

## Querying Events

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/structural-events` | List structural events (filterable by entity type) |
| `GET` | `/api/products/:id/activities` | List activities for a product |
| `GET` | `/api/objectives/:id/history` | List history for an objective |

---

## What Events Do Not Do

- **Do not trigger actions.** Events are records, not triggers. They do not initiate workflows or notifications.
- **Do not aggregate.** Events are stored individually. Aggregation (counts, trends) is performed at query time.
- **Do not expire.** Events are retained indefinitely for audit purposes.
- **Do not contain source data.** Events contain metadata about changes (field names, old/new values) but not the underlying data being governed.
