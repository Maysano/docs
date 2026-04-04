# Product Templates

Product Templates in Maysano provide a starting point for creating new data products. They encode organizational patterns, best practices, and default configurations — reducing the time and effort needed to create well-governed products.

---

## What Templates Are

A template is a predefined product skeleton. It includes default values for product fields, governance component suggestions, and structural patterns that reflect how the organization typically builds data products.

Templates are created and maintained by the **System Steward**. They represent codified governance intent: "When you create a product of this type, start with these defaults."

---

## Template Structure

| Field | Description |
|---|---|
| `name` | Template name (e.g. "Standard Dataset", "API Product", "Compliance Report") |
| `description` | When and why to use this template |
| `type` | Product type this template applies to (e.g. `dataset`, `api`, `stream`, `report`) |
| `defaultSpecification` | Pre-filled ODPS specification (JSON) with default values |

---

## Template Types

Templates can be created for any product type. Common examples:

| Template | Type | Includes |
|---|---|---|
| **Standard Dataset** | `dataset` | Default schema structure, standard DQ dimensions, internal visibility |
| **External API Product** | `api` | Access profile suggestions, SLA defaults, rate limiting guidance |
| **Compliance Report** | `report` | Mandatory quality dimensions, audit-friendly metadata, compliance tags |
| **Real-Time Stream** | `stream` | Timeliness-focused DQ targets, low-latency SLA defaults |

---

## Default Specification

The `defaultSpecification` field contains a pre-filled ODPS specification. When a user creates a product from a template, this specification is copied into the new product as a starting point.

The default specification can include:

- Pre-filled metadata fields (type, visibility, tags)
- Suggested governance component configurations
- Placeholder descriptions with guidance text
- Standard schema patterns

Users are expected to customize the specification. The template provides structure, not final content.

---

## Creating Templates

Templates are created by the System Steward through the Governance Library:

1. Define the template name, description, and type.
2. Build the default specification with appropriate defaults.
3. Save the template to the library.

Templates do not have a lifecycle or versioning — they are living documents that can be updated at any time. Changes to a template do not affect products already created from it.

---

## Using Templates

When creating a new data product:

1. Select a template from the available options.
2. The template's default specification is copied into the new product.
3. Customize the product: edit fields, attach governance components, add content schema.
4. Save and continue the product lifecycle.

The template is a one-time copy. After creation, the product is independent of the template.

---

## What Templates Do Not Do

- **Do not enforce structure.** Templates provide defaults, not constraints. Users can modify any field.
- **Do not auto-update products.** Updating a template does not change existing products.
- **Do not attach governance components.** Templates may suggest components, but attachment is a separate action.
- **Do not replace governance review.** A product created from a template still requires human review and approval before publication.
