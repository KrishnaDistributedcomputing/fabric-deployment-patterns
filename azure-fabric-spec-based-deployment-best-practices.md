# Azure Fabric Spec-Based Deployment Best Practices

## Purpose

Use a spec-based deployment model to make Microsoft Fabric environments repeatable, reviewable, auditable, and promotion-ready across development, test, and production. The deployment spec should describe the target state, while automation tools apply that state consistently.

## Core Principles

| Principle | Practice |
| --- | --- |
| Declarative target state | Define workspaces, capacities, security, data products, and deployment settings in version-controlled specs. |
| Environment parity | Keep dev, test, and prod structurally consistent; vary only approved parameters such as capacity size, workspace names, and connection targets. |
| Separation of duties | Separate platform foundation, workspace provisioning, data engineering assets, and reporting assets into clear deployment scopes. |
| Least privilege | Use Microsoft Entra ID groups, managed identities, and service principals with the minimum required permissions. |
| Policy-driven governance | Enforce naming, tagging, data classification, sensitivity labels, and workspace ownership through standards and review gates. |
| Promotion over mutation | Promote tested changes through environments instead of manually changing production. |
| Observable operations | Capture deployment logs, capacity metrics, refresh history, lineage, and security audit events. |

## Recommended Repository Structure

```text
fabric-deployment-patterns/
  README.md
  fabric-deployment-phases.md
  fabric-cost-model.md
  specs/
    dev.fabric.yaml
    test.fabric.yaml
    prod.fabric.yaml
  deployment/
    pipelines/
    scripts/
    parameters/
  governance/
    naming-standards.md
    access-model.md
    workspace-standards.md
  operations/
    monitoring.md
    runbook.md
```

## Deployment Spec Contents

A Fabric deployment spec should capture the minimum approved target state for each environment.

| Spec Section | Required Content |
| --- | --- |
| Environment | Environment name, region, subscription, tenant, deployment ring, approval requirements |
| Capacity | Fabric capacity SKU, assignment rules, scaling policy, pause/resume policy for non-production |
| Workspaces | Workspace names, descriptions, domains, owners, capacity assignment, deployment pipeline stage |
| Identity | Admin groups, contributor groups, viewer groups, service principals, managed identities |
| Security | Sensitivity labels, item permissions, data access groups, private connectivity requirements |
| Data Products | Lakehouses, warehouses, semantic models, reports, notebooks, pipelines, shortcuts |
| Connections | Data source references, gateway usage, credential ownership, Key Vault references |
| Governance | Naming standards, tagging, retention, endorsement, lineage, audit requirements |
| Operations | Monitoring targets, alert rules, refresh windows, incident contacts, rollback approach |

## Example Spec Pattern

```yaml
environment: dev
tenant: contoso.onmicrosoft.com
region: eastus

capacity:
  name: fab-dev-capacity
  sku: F2
  schedule: business-hours

workspaces:
  - name: fab-dev-sales-analytics
    domain: sales
    capacity: fab-dev-capacity
    owners:
      - entra-group:fabric-platform-admins-dev
    contributors:
      - entra-group:fabric-sales-engineers-dev
    viewers:
      - entra-group:fabric-sales-readers-dev
    items:
      lakehouses:
        - sales_bronze_lh
        - sales_silver_lh
      warehouses:
        - sales_curated_wh
      pipelines:
        - ingest_sales_orders
      semanticModels:
        - sales_performance_model

governance:
  sensitivityLabel: Confidential
  retentionDays: 365
  endorsement: Promoted
  auditEnabled: true
```

## Azure Foundation Best Practices

- Use separate subscriptions or management groups where organizational policy requires environment isolation.
- Use Microsoft Entra ID groups for all human access; avoid direct user assignments.
- Use service principals or managed identities for automation.
- Store secrets and connection material in Azure Key Vault or approved secret stores.
- Apply Azure Policy for required tags, allowed regions, private endpoint requirements, and diagnostic settings where applicable.
- Standardize naming across capacity, workspace, data products, service principals, and resource groups.
- Capture cost allocation tags for environment, domain, application, owner, and cost center.

## Microsoft Fabric Best Practices

- Use Fabric deployment pipelines or Git integration for controlled promotion of Fabric items.
- Keep production changes pull-request driven and approval gated.
- Assign workspaces to capacity through the deployment spec rather than ad hoc portal changes.
- Separate domain workspaces from shared platform/admin workspaces.
- Use OneLake shortcuts intentionally to avoid duplicate data copies.
- Define workspace roles through Entra groups aligned to owner, contributor, member, and viewer access patterns.
- Standardize lakehouse zones such as bronze, silver, and gold where the data architecture requires medallion layering.
- Track semantic models, reports, data pipelines, notebooks, lakehouses, warehouses, and shortcuts as deployable assets.
- Validate tenant settings, workspace settings, and capacity settings before production rollout.

## CI/CD Best Practices

| Stage | Gate |
| --- | --- |
| Pull request | Spec validation, naming validation, security review, cost-impact review |
| Dev deployment | Automated deployment from approved branch |
| Test deployment | Integration testing, refresh validation, access validation, performance checks |
| Production deployment | Change approval, release notes, rollback plan, business sign-off |
| Post-deployment | Smoke test, audit log review, monitoring confirmation, cost baseline update |

## Validation Checklist

- Spec syntax is valid and reviewed.
- Workspace names, owners, domains, and capacity assignments match standards.
- Entra groups exist and are mapped to the correct roles.
- Data source connections use approved credential and secret patterns.
- No production secrets are committed to Git.
- Deployment produces repeatable results when re-run.
- Fabric items are promoted through approved deployment stages.
- Capacity utilization and refresh performance are monitored after deployment.
- Cost model is updated when capacity, storage, or licensing assumptions change.

## Operational Controls

- Maintain a rollback plan for each production deployment.
- Require peer review for spec changes affecting production access, cost, or data exposure.
- Record deployment evidence, approvals, and validation results.
- Review access and workspace ownership at least quarterly.
- Review capacity utilization monthly and resize based on measured workload demand.
- Keep deployment specs aligned with the current-state inventory and target architecture.

## Definition of Done

A Fabric deployment is complete when the target environment matches the approved spec, production access is group-based, data products are validated, monitoring is active, cost assumptions are updated, and business sign-off is recorded.
