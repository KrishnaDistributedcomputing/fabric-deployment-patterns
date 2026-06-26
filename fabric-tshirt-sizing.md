# Fabric Deployment T-Shirt Sizing

## Purpose

Use T-shirt sizing to estimate Microsoft Fabric deployment complexity, delivery effort, capacity planning, governance needs, and rollout risk before detailed design is complete. These sizes are planning ranges; validate them during the current-state assessment and PoC.

## Sizing Dimensions

| Dimension | What To Assess |
| --- | --- |
| Business domains | Number of domains, data product owners, and stakeholder groups |
| Workspaces | Number of dev, test, prod, sandbox, and shared workspaces |
| Data sources | Number and complexity of source systems, gateways, APIs, files, and databases |
| Data volume | Initial storage, daily ingest, retention, and growth expectations |
| Data movement | Pipeline frequency, orchestration complexity, transformation needs, and SLAs |
| Power BI assets | Reports, semantic models, refresh schedules, consumers, and authors |
| Security | Sensitivity labels, row-level security, object-level security, external sharing, and audit requirements |
| Governance | Domains, naming standards, endorsement, ownership, lineage, retention, and access reviews |
| Environments | Dev/test/prod separation, deployment pipelines, Git integration, and release approvals |
| Operations | Monitoring, support hours, incident response, capacity reviews, and runbooks |

## T-Shirt Size Summary

| Size | Best Fit | Typical Scope | Delivery Complexity |
| --- | --- | --- | --- |
| XS | Discovery or sandbox | 1 workspace, limited sample data, no production users | Very low |
| S | Department PoC | 1 domain, 2-3 workspaces, a few data sources, limited reporting | Low |
| M | Department production | 1-2 domains, dev/test/prod, governed reports, repeatable deployment | Medium |
| L | Multi-domain platform | 3-5 domains, multiple production workloads, formal governance and operations | High |
| XL | Enterprise platform | 5+ domains, regulated data, large migration, broad adoption, enterprise operations | Very high |

## Detailed Sizing Matrix

| Sizing Area | XS | S | M | L | XL |
| --- | --- | --- | --- | --- | --- |
| Business domains | 0-1 | 1 | 1-2 | 3-5 | 5+ |
| Workspaces | 1 | 2-3 | 4-8 | 9-20 | 20+ |
| Environments | Sandbox only | Dev and PoC | Dev/test/prod | Dev/test/prod plus shared services | Enterprise environment model with multiple rings |
| Data sources | 1 | 2-3 | 4-8 | 9-20 | 20+ |
| Initial data volume | Less than 100 GB | 100 GB-1 TB | 1-5 TB | 5-25 TB | 25+ TB |
| Daily ingest | Less than 5 GB | 5-25 GB | 25-100 GB | 100-500 GB | 500+ GB |
| Power BI reports | 1-5 | 5-20 | 20-75 | 75-250 | 250+ |
| Semantic models | 1 | 1-3 | 3-10 | 10-30 | 30+ |
| Pipelines | 1-3 | 3-10 | 10-30 | 30-100 | 100+ |
| Security complexity | Basic workspace roles | Group-based access | RLS/OLS and labels | Regulated data and audit controls | Enterprise compliance and data protection controls |
| Governance | Minimal | Basic standards | Standardized domains and ownership | Formal governance framework | Enterprise operating model |
| CI/CD | Manual or none | Basic promotion | Git integration and deployment pipelines | Release gates and approvals | Enterprise release management |
| Operations | Ad hoc | Basic monitoring | Runbooks and alerts | Defined support model | 24x7 or enterprise support model |

## Effort Estimate Ranges

| Size | Typical Duration | Delivery Effort | Platform Roles Usually Needed |
| --- | --- | --- | --- |
| XS | 1-2 weeks | 5-15 person-days | Fabric architect, data engineer |
| S | 3-6 weeks | 20-45 person-days | Fabric architect, data engineer, Power BI developer |
| M | 6-12 weeks | 60-120 person-days | Architect, data engineer, Power BI developer, security, platform admin |
| L | 3-6 months | 150-350 person-days | Architecture, engineering, BI, security, governance, operations, project management |
| XL | 6-12+ months | 400+ person-days | Enterprise architecture, platform team, domain teams, security, governance, operations, change management |

## Capacity Planning Guidance

| Size | Starting Capacity Planning Approach | Validation Guidance |
| --- | --- | --- |
| XS | Use the smallest practical capacity or trial/sandbox approach where appropriate | Validate feature fit, not production performance |
| S | Start small and schedule non-production capacity where possible | Measure refresh duration, query performance, and peak usage during PoC |
| M | Size separate dev/test/prod needs and baseline production concurrency | Use Fabric capacity metrics before production launch |
| L | Model workload classes separately: ingestion, engineering, warehouse, semantic/reporting | Load test critical refresh and query windows |
| XL | Build capacity strategy by domain, workload criticality, and operating model | Establish monthly capacity review, chargeback/showback, and scaling rules |

## Cost Model Mapping

| Size | Cost Model Expectation |
| --- | --- |
| XS | Use for learning and validation; do not treat as production TCO. |
| S | Estimate PoC cost and first production candidate cost separately. |
| M | Build first-year, three-year, and five-year TCO using measured PoC consumption. |
| L | Include platform operations, governance, security review, and migration factory costs. |
| XL | Include enterprise support, program management, change management, compliance, and multi-domain operations. |

## Recommended Deployment Pattern By Size

| Size | Deployment Pattern |
| --- | --- |
| XS | Single sandbox workspace, limited sample data, manual validation. |
| S | Department PoC with basic workspace standards and documented go/no-go criteria. |
| M | Governed departmental production deployment with dev/test/prod, Git integration, deployment pipeline, and runbook. |
| L | Multi-domain platform deployment with standard workspace factory, domain model, release gates, monitoring, and access reviews. |
| XL | Enterprise Fabric program with formal landing zone, domain onboarding factory, centralized governance, federated ownership, and operational service management. |

## Sizing Questions

- How many business domains and data product owners are in scope?
- How many reports, semantic models, pipelines, lakehouses, and warehouses will be migrated or created?
- What are the daily ingest volume, retention requirements, and expected growth rate?
- What are the refresh, query, and reporting SLAs?
- Which workloads require regulated-data controls, sensitivity labels, RLS/OLS, or audit evidence?
- Is dev/test/prod separation required from day one?
- Will deployment use Git integration, Fabric deployment pipelines, and pull-request approvals?
- What support model is required after production launch?

## Sizing Decision Rule

Choose the larger size when two or more sizing dimensions land in a higher category. Reassess the size after current-state assessment, after architecture design, and after PoC performance validation.
