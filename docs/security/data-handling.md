# Data Handling

This page describes how Maysano stores, processes, and protects data within the platform.

---

## Data Storage

Maysano uses PostgreSQL as its primary data store. All platform data — products, governance components, KPIs, user accounts, activity logs, and configuration — is stored in a single PostgreSQL database.

### What Is Stored

| Data Category | Examples | Storage |
|---|---|---|
| Product metadata | Names, descriptions, specifications, tags, lifecycle state | PostgreSQL (jsonb for specifications) |
| Governance components | DQ Profiles, SLA Profiles, Access Profiles, Pricing Plans | PostgreSQL |
| Quality check results | Scores, pass/fail status, execution timestamps | Quality platform (external) |
| User accounts | Email, name, hashed password, roles | PostgreSQL |
| Session data | Login sessions, session tokens | PostgreSQL (via connect-pg-simple) |
| Activity logs | Product changes, objective updates, structural events | PostgreSQL |
| AI conversations | Chat messages, session metadata | PostgreSQL |
| Guidance rulesets | Published rule snapshots | PostgreSQL |

### What Is Not Stored

- **Source data.** Maysano does not copy, cache, or store data from your databases, warehouses, or lakes.
- **DQ check execution data.** Raw query results from quality checks are stored in the quality platform, not in Maysano.
- **External system credentials in plaintext.** Credentials for OpenMetadata and other integrations are stored encrypted.

---

## PII Handling

Maysano provides PII awareness at the content schema level:

- Each content field in a product schema can be flagged with `piiFlag: true`.
- Sensitivity levels (`public`, `internal`, `confidential`, `restricted`) can be assigned to each field.
- These flags are governance metadata — they inform data handling policies but do not enforce them at the data layer.

The platform itself stores minimal PII: user email addresses, first/last names, and optionally profile images. No customer business data passes through Maysano.

---

## Credential Management

### Database Connections

Quality platform connection credentials (host, port, database, username, password) are configured through environment variables. They are:

- Never stored in application code
- Never logged (passwords are excluded from debug output)
- Transmitted over the internal network to the quality platform API

### External Integrations

- **OpenMetadata** — Connection credentials are stored encrypted in the database (`credentialsEncrypted` field).
- **GitHub** — OAuth access tokens are stored in the database, scoped to the user who authorized the connection.
- **LLM Provider** — API keys are configured as environment variables and never stored in the database.

---

## Password Security

User passwords are managed through the authentication system:

- Passwords are hashed before storage (never stored in plaintext).
- Password changes require the current password for verification.
- Session-based authentication eliminates the need for passwords in API calls after login.

---

## API Validation

All API endpoints enforce input validation:

- Request bodies are validated against Zod schemas before processing.
- Invalid requests receive a 400 response with structured error details.
- Protected endpoints require authentication (session-based).
- The platform does not accept or process requests without valid session tokens for protected resources.

---

## Data Lifecycle

| Event | Data Behavior |
|---|---|
| Product created | Metadata stored in PostgreSQL |
| Product versioned | Immutable snapshot created and stored |
| Product retired | Metadata preserved for audit trail; not deleted |
| User deleted | Account marked as deleted; data preserved for audit |
| Governance component retired | Component preserved for historical reference |

Maysano does not automatically delete data. Retention is designed to support audit trails and governance history.

---

## What Data Handling Does Not Cover

- **Data encryption at rest.** This is a database infrastructure concern. PostgreSQL encryption (TDE, pgcrypto) is configured at the infrastructure level.
- **Data encryption in transit.** HTTPS/TLS is configured at the infrastructure and hosting level.
- **Data residency.** Where the database is hosted determines data residency. This is a deployment decision, not a platform feature.
- **Backup and recovery.** Database backups are an infrastructure responsibility.
