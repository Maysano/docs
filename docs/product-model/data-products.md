# Data Products


## 1. Overview

A **Data Product** is a well-defined, managed, and governed collection of data that serves a specific business purpose. Within this application, data products follow the **Open Data Product Standard (ODPS) version 4.1**, which ensures that every product is described consistently with clear ownership, quality commitments, and strategic alignment.

The **Manage Data Products** group in the sidebar gives you access to the tools you need to create, organise, and monitor all your data products. It contains the following pages:

| Page | Purpose |
|------|---------|
| **Data Products** | The central listing of all your data products, with multiple viewing options |
| **Start from Requirements** | Upload a requirements document and let the system draft a data product for you |
| **Workflows** | Manage automated processes related to data products |

---

## 2. The Data Products Listing Page

This is the main hub where you see all existing data products at a glance. The page title reads **"Data Products"** and its subtitle describes it as the place to *"Manage and explore your organisation's data products."*

### 2.1 View Modes

You can switch between three different ways to visualise your products using the toggle buttons in the toolbar:

- **Grid View** — Products are shown as individual cards arranged in a responsive grid. Each card displays the product name, description, status, type, visibility, version, owner, and last updated time. This is the default view.

- **List View** — Products are presented in a table format with columns for Product, Status, Type, Visibility, Owner, Version, and Last Updated. This is ideal when you need to scan many products quickly or compare details side by side.

- **Kanban View** — Products are arranged into columns based on their lifecycle stage (Draft, Development, Testing, Acceptance, Production, Sunset, Retired). You can drag and drop products between columns to change their status, and reorder products within a column. See [Section 11 — The Kanban Board](#11-the-kanban-board) for more detail.

Your selected view mode is remembered between sessions, so it will be the same the next time you come back.

### 2.2 Search

A search bar at the top of the page lets you find products by name, description, or product ID. Simply type in the search box and the list updates instantly to show only matching results.

### 2.3 Filters

Two dropdown filters are available:

- **Status Filter** — Narrow the list to products at a specific lifecycle stage: Draft, Development, Testing, Acceptance, Production, Sunset, or Retired. Select "All Status" to remove this filter.

- **Type Filter** — Narrow the list to a specific type of data product. Available types include:
  - Raw Data
  - Derived Data
  - Dataset
  - Reports
  - Analytic View
  - 3D Visualisation
  - Algorithm
  - Decision Support
  - Automated Decision-Making
  - Data-Enhanced Product
  - Data-Driven Service
  - Data-Enabled Performance
  - Bi-Directional

### 2.4 Sorting

You can sort the visible products in four ways:

- **Newest First** (default) — Most recently created products appear at the top.
- **Oldest First** — The oldest products appear at the top.
- **A to Z** — Sorted alphabetically by product name.
- **Z to A** — Reverse alphabetical order.

### 2.5 Product Actions (View, Edit, Delete)

Each product card or row has a three-dot menu that provides quick actions:

- **View Details** — Opens the full product viewer page (see [Section 5](#5-viewing-a-data-product-product-viewer)).
- **Edit** — Opens the product editor to make changes (see [Section 6](#6-editing-a-data-product)).
- **Delete** — Removes the product. A confirmation dialog appears before the deletion is carried out, to prevent accidental removal.

Additionally, two buttons at the top of the page allow you to:

- **Draft from Requirements** — Takes you to the document upload page to automatically draft a product from an uploaded requirements file.
- **Create Product** — Opens the step-by-step product builder to create a new product from scratch.

---

## 3. Creating a Data Product (Product Builder)

The Product Builder guides you through a five-step wizard to create a new data product. Each step focuses on a different aspect of the product definition, and you can navigate back and forth between completed steps.

### 3.1 Step 1 — Basic Information

This is where you define the essential identity of your data product:

- **Product Name** — A clear, descriptive name (e.g., "Customer Analytics Dataset"). Required.
- **Product ID** — A unique technical identifier using lowercase letters, numbers, and dashes (e.g., "customer-analytics-dataset"). Required.
- **Description** — A free-text explanation of what this data product is, what data it contains, and what business value it provides.
- **Owner** — The person responsible for this product. You can select from team members who have been configured in your company profile.
- **Version** — The initial version number, which defaults to "1.0.0".

### 3.2 Step 2 — Classification

This step defines how your product is categorised and who can see it:

- **Product Type** — The kind of data product you are creating. Options range from basic types like "Raw Data" and "Dataset" to more advanced types like "Algorithm", "Decision Support", and "Data-Driven Service".
- **Visibility** — Who can discover and access this product:
  - *Private* — Only you, the creator
  - *Invitation* — Only people you explicitly invite
  - *Organisation* — Everyone in your organisation
  - *Dataspace* — All members of your data space
  - *Public* — Anyone, openly accessible
- **Status** — The initial lifecycle stage. New products typically start as "Draft" (see [Section 7 — Lifecycle Stages](#7-lifecycle-stages)).

### 3.3 Step 3 — Strategy (Objectives and KPIs)

This step connects your data product to your organisation's strategic goals:

- **Business Objectives** — Define what business goals this product supports (e.g., "Increase customer retention by 15%"). Each objective has a title, description, priority level (High, Medium, Low), and status.
- **KPIs (Key Performance Indicators)** — Define measurable targets that track how well the product is performing (e.g., "Data freshness: target 99% within 1 hour"). Each KPI includes a name, description, measurement unit, target value, and measurement frequency.

There are three ways to populate this section:
1. **Create New** — Manually add objectives and KPIs from scratch.
2. **Select Existing** — Pick from objectives and KPIs that have already been defined elsewhere in the application (e.g., in the Business Objectives or KPI Builder pages).
3. **AI Generate** — Let the AI assistant automatically generate relevant objectives and KPIs based on your product's name, description, and type.

### 3.4 Step 4 — Governance (SLA, Data Quality, Access)

This step attaches governance profiles that define your commitments for this product:

- **Service Level Agreement (SLA)** — Select a pre-defined SLA profile that specifies commitments like uptime, response time, latency, error rate, and update frequency. SLA profiles are created in the Components Library.
- **Data Quality Profile** — Select a profile that defines quality standards such as accuracy, completeness, consistency, timeliness, conformity, coverage, validity, and uniqueness. These are also created in the Components Library.
- **Access Profile** — Select a profile that specifies how consumers will access the data (e.g., API, file download) including authentication method and data format.

If no profiles exist yet, the system will guide you to create them in the Components Library first.

When the product builder detects imported metadata (e.g., from OpenMetadata), it may also suggest appropriate SLA and data quality profiles based on the quality characteristics of the source data.

### 3.5 Step 5 — Review and Create

The final step presents a summary of everything you have configured. You can review all fields, go back to any previous step to make corrections, and then click **Create** to save the product. After creation, you are taken directly to the new product's detail page.

---

## 4. Start from Requirements (Document Upload)

This feature allows you to skip the manual product builder by uploading a requirements document. The process works in three stages:

1. **Upload** — Drag and drop or browse to select one or more requirements documents. The system extracts the text content from your files.
2. **Creating** — The system parses the extracted text to populate a draft product specification. It looks for patterns such as product name, purpose, target users, data sources, and quality requirements within the document text, and maps them to the corresponding data product fields.
3. **Review** — You review the generated draft, which includes a pre-filled name, product ID, description, type, tags, and a basic strategy with default objectives and KPIs. You can edit any field, change the product type, and optionally apply a pre-existing template before saving it as a new data product.

You can also search and select from existing templates to use as a starting point. This is especially useful when your organisation has standardised formats for certain types of data products.

---

## 5. Viewing a Data Product (Product Viewer)

Clicking on any product opens its full detail page. The page header shows the product name, status, type, product ID, and current version. It also indicates a "readiness" status showing how complete the product definition is (e.g., "3/5 Complete" or "Ready to Advance").

The product viewer is organised into tabs:

### 5.1 Overview Tab

Provides a comprehensive snapshot of the product:

- **Product Details** — Name, Product ID, Type, Visibility, Owner, Current Version, Created By, and Creation Date.
- **Description** — The full text description of what this product is.
- **Business Context** — If business objectives are linked, they are displayed here with their priority and status.
- **Quick Summary** — Three summary cards showing:
  - *Governance*: Which SLA and Data Quality profiles are attached
  - *Strategy*: Number of objectives and KPIs
  - *Specification*: Number of content fields and published versions
- **Dependencies** — Lists other products or resources this product depends on.

### 5.2 Governance Tab

Shows the governance commitments attached to this product in detail:

- **SLA Commitments** — Displays the selected SLA profile with its specific metrics (uptime, latency, response time, error rate, update frequency, etc.). Each metric is shown in a clear, labelled card.
- **Data Quality Promises** — Displays the selected Data Quality profile with dimensions like accuracy, completeness, consistency, timeliness, uniqueness, conformity, coverage, and validity.
- **Access Configuration** — Shows the selected Access profile including protocol, authentication method, and data format.

Each section has an "Edit" link that takes you directly to the Governance step of the product editor.

### 5.3 Strategy Tab

Displays the business strategy information linked to this product:

- **Business Objectives** — All linked objectives with their title, description, priority, and status.
- **Product KPIs** — All KPIs with their name, description, target value, current value, unit, and measurement frequency.

### 5.4 Specification Tab

This tab displays the generated ODPS 4.1 specification for your product. The specification includes all the product details, governance commitments, and strategy information formatted according to the standard.

From this tab, you can:
- **Copy** the specification to your clipboard.
- **Download** the specification as a YAML file.
- View both YAML and JSON representations of the spec.

This tab may be hidden for certain user roles (e.g., Product Managers) who do not need direct access to the technical specification.

### 5.5 History Tab

Shows the version history and GitHub activity for the product:

- **Published Versions** — A timeline of all published versions with their version number, changelog description, and publication date. You can expand each version to see its full details.
- **GitHub History** — If a GitHub repository is linked, this section shows recent commits related to this product, including commit messages, authors, and links to GitHub.

### 5.6 Comments Tab

A collaboration space for team members to discuss the product:

- **Discussion Threads** — Each thread has a title, category (e.g., General, Quality, Governance), and a creation date. You can create new threads by providing a title and selecting a category.
- **Messages** — Within each thread, team members can post replies. Each message shows the author's name, role, and timestamp.

This feature enables structured conversations around specific aspects of the product, helping teams coordinate decisions and track rationale.

---

## 6. Editing a Data Product

The product editor uses the same five-step wizard format as the product builder, but pre-populated with the existing product's data. You can:

- Navigate freely between the five steps using the step indicator at the top.
- Make changes to any field and see an "Unsaved changes" indicator.
- Click **Save Changes** at any point to persist your updates.
- The editor validates each step before allowing you to proceed, just like the builder.

The steps are identical to those in [Section 3 — Creating a Data Product](#3-creating-a-data-product-product-builder): Basic Info, Classification, Strategy, Governance, and Review.

---

## 7. Lifecycle Stages

Every data product goes through a defined lifecycle. The stages represent the maturity and readiness of the product:

| Stage | Meaning |
|-------|---------|
| **Draft** | The product is being defined. Information may be incomplete. |
| **Development** | The product is actively being built or configured. |
| **Testing** | The product is undergoing quality and validation checks. |
| **Acceptance** | Stakeholders are reviewing the product before it goes live. |
| **Production** | The product is live, actively maintained, and available to consumers. |
| **Sunset** | The product is scheduled for retirement. Consumers should plan to migrate. |
| **Retired** | The product is no longer available or maintained. |

### 7.1 Advancing Through Stages

From the product viewer, you can advance a product to its next lifecycle stage using the **"Advance to [Next Stage]"** button. This button is only available if:
- You have the appropriate permissions (Product Manager or similar role).
- The product meets the readiness criteria for the current stage.

The progression follows the sequence: Draft > Development > Testing > Acceptance > Production.

### 7.2 Readiness Checks

Before a product can be advanced, the system checks whether certain criteria are met. This is shown as a readiness indicator (e.g., "3/5 Complete" or "Ready to Advance"). The checks verify that essential fields such as governance profiles, strategy definitions, and core product details are properly filled in.

---

## 8. Version Management

Version management allows you to create formal, immutable snapshots of your data product at specific points in time.

### 8.1 Publishing a Version

Click **Publish Version** from the product viewer to create a new version. You will need to:

1. **Specify a version number** — The system suggests the next version automatically (e.g., if the current version is 1.0.0, it suggests 1.1.0), but you can override it.
2. **Write a changelog** — Describe what changed in this version. This is required.
3. Click **Publish** to create the version.

Published versions are immutable — they cannot be edited after creation. They serve as an official record of the product's state at that point.

### 8.2 Drafting a New Version

After publishing a version, you can click **Draft New Version** to create a new working copy. This bumps the version number and allows you to make further changes before the next publication.

### 8.3 Version History

All published versions are listed in the History tab of the product viewer. Each entry shows the version number, who published it, when it was published, and the changelog entry. You can expand a version to see its full details.

---

## 9. GitHub Integration

Data products can be linked to a GitHub repository for source control and collaboration with development teams.

### 9.1 Linking a Repository

From the product viewer, click **Link Repository** to connect the product to a GitHub repository. You will see a list of available repositories from your connected GitHub account. Select the repository you want to link.

Prerequisites: Your GitHub account must be connected via the application's GitHub integration settings.

### 9.2 Pushing to GitHub

Once linked, you can push the product's ODPS specification (both YAML and JSON formats) to the GitHub repository. You can choose which branch to push to. The files are stored in a structured path: `products/[product-id]/odps.yaml` and `products/[product-id]/odps.json`.

### 9.3 Pulling from GitHub

You can pull specification changes back from GitHub into the application. This is useful when the specification has been edited directly in the repository by developers or through a pull request workflow.

### 9.4 Creating Pull Requests

You can create a GitHub Pull Request directly from the application. This opens a PR in the linked repository, making it easy to propose specification changes for review by your development team.

---

## 10. ODPS 4.1 Specification Export

Every data product automatically generates an **Open Data Product Standard (ODPS) 4.1** compliant specification. This specification includes:

- **Product Details** — Name, ID, visibility, status, type, description, and version.
- **Data Holder** — Organisation and owner information.
- **Product Strategy** — Business objectives and KPIs (when defined).
- **SLA** — Service level commitments with specific dimensions and targets (when an SLA profile is attached).
- **Data Quality** — Quality dimensions with targets for accuracy, completeness, consistency, and more (when a Data Quality profile is attached).
- **Data Access** — Access method details including protocol, authentication, and format (when an Access profile is attached).

The specification can be:
- Viewed in YAML or JSON format in the Specification tab.
- Copied to your clipboard.
- Downloaded as a file.
- Pushed to a linked GitHub repository.

---

## 11. The Kanban Board

The Kanban view provides a visual, drag-and-drop way to manage products across their lifecycle stages.

**How it works:**

- Each lifecycle stage (Draft, Development, Testing, Acceptance, Production, Sunset, Retired) is represented as a column.
- Products appear as cards within their respective stage column.
- **Drag and drop** a product card from one column to another to change its lifecycle status instantly.
- **Reorder** products within a column by dragging them up or down. The order is saved automatically.

Each Kanban card shows:
- Product name and ID
- Current version
- Owner
- Last updated time
- A menu for quick actions (View, Edit, Delete)

The Kanban board respects any active search queries and filters, so you will only see products that match your current filter criteria.

---

## 12. Data Product Catalog (Consumer View)

While the **Manage Data Products** section is where you create and manage products, the **Data Product Catalog** (accessible from the sidebar under its own entry) is the consumer-facing marketplace view. It is worth mentioning here because it directly relates to managed data products.

The catalog:
- Only shows products that have reached the **Production** lifecycle stage.
- Highlights **Featured Products** — those that are both in Production and set to Public visibility.
- Displays each product with consumer-relevant indicators: view count, number of consumers, data freshness, and quality score. (Note: some of these metrics are currently illustrative placeholders and will be connected to live data sources in a future update.)
- Provides search, sorting (Most Recent, Most Popular, Highest Quality), and domain-based filtering. Domain filters are derived from product tags.
- Links to a detailed catalog page for each product where consumers can explore its specifications, governance commitments, and usage information.

This separation between management and catalog views ensures that only polished, production-ready products are visible to data consumers, while teams have full flexibility to work on drafts and in-progress products privately.


