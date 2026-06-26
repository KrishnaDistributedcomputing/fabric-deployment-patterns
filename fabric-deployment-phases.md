# Fabric Deployment Phases

This deployment pattern follows Microsoft-aligned practices for planning, governing, deploying, validating, and operating Microsoft Fabric. It emphasizes tenant governance, Microsoft Entra ID access control, Fabric capacity planning, OneLake architecture, deployment pipelines, Git integration, security validation, and operational monitoring.

---

# Phase 2 - Current State Assessment

## Objectives

Understand the existing analytics estate, identify migration readiness, and create a fact-based baseline for Microsoft Fabric architecture, cost, governance, and deployment planning.

## Microsoft Best Practices

- Inventory Power BI workspaces, reports, semantic models, dataflows, gateways, refresh schedules, tenant settings, endorsement status, and workspace ownership.
- Assess Synapse, SQL, data warehouse, data lake, ETL, and reporting workloads by business domain, criticality, data volume, refresh frequency, peak usage, and compliance requirements.
- Use Microsoft Entra ID groups as the target access model; identify direct user assignments that should be remediated.
- Review sensitivity labels, data classification, retention needs, audit requirements, and Purview or governance integration points.
- Capture current capacity usage, refresh failures, query performance issues, gateway dependencies, and operational support pain points.
- Identify workloads that should be retired, consolidated, migrated, modernized, or left in place.

## Activities

- Power BI inventory
- Synapse assessment
- Data warehouse assessment
- ETL and pipeline assessment
- Gateway and data source assessment
- Security and access review
- Tenant and workspace governance review
- Capacity and performance review
- Compliance, audit, and retention review
- Migration complexity scoring

## Deliverables

- Current State Architecture
- Workload and Asset Inventory
- Migration Readiness Assessment
- Gap Analysis
- Risk Register
- Initial Capacity and Licensing Baseline
- Governance Findings

## Exit Criteria

- Current workloads and dependencies are documented.
- Security, governance, and compliance gaps are known.
- Initial capacity, licensing, and migration assumptions are ready for architecture design.

---

# Phase 3 - Architecture and Design

## Objectives

Define the target Microsoft Fabric architecture and deployment model using repeatable, governed, and environment-aware design standards.

## Microsoft Best Practices

- Design around OneLake as the logical data foundation and avoid unnecessary data copies by using shortcuts where appropriate.
- Use domains and workspaces to align Fabric assets to business ownership, data products, lifecycle, and security boundaries.
- Separate development, test, and production environments using Fabric deployment pipelines, Git integration, and approved branch policies.
- Define lakehouse, warehouse, semantic model, notebook, pipeline, and report patterns by workload type rather than using a single design for every scenario.
- Standardize medallion or equivalent data zones where the data platform needs raw, cleansed, curated, and consumption layers.
- Use Microsoft Entra ID groups for workspace roles and avoid direct user permissions in production.
- Plan tenant settings, workspace settings, capacity assignment, data source connections, private connectivity, sensitivity labels, and endorsement rules before build.
- Define monitoring requirements for capacity metrics, refresh history, pipeline runs, user activity, audit events, and data quality checks.

## Activities

- OneLake architecture
- Lakehouse and warehouse design
- Data Factory and pipeline design
- Semantic model and Power BI design standards
- Workspace, domain, and environment design
- Security architecture
- Governance and compliance design
- CI/CD and Git integration design
- Monitoring and operations design
- Disaster recovery and rollback design

## Deliverables

- Target Architecture
- Design Decisions
- Deployment Model
- Workspace and Domain Strategy
- Identity and Access Model
- Data Classification and Sensitivity Label Model
- CI/CD and Promotion Strategy
- Monitoring and Operations Model

## Exit Criteria

- Target architecture is approved by platform, security, data, and business stakeholders.
- Deployment approach is defined for dev, test, and production.
- Governance controls are mapped to tenant, capacity, workspace, and item-level responsibilities.

---

# Phase 4 - Business Case and ROI

## Objectives

Build a defensible business case for Microsoft Fabric based on cost, licensing, migration value, operational efficiency, and measurable business outcomes.

## Microsoft Best Practices

- Estimate Fabric capacity using measured workload characteristics, not only user count.
- Separate one-time migration cost from monthly run cost.
- Compare pay-as-you-go, reserved capacity, scale-up/scale-down, and non-production scheduling scenarios.
- Include Power BI licensing, Fabric capacity, OneLake storage, networking, monitoring, operations, implementation, testing, and enablement costs.
- Quantify benefits from platform consolidation, reduced duplicate data, faster delivery, improved governance, and lower operational overhead.
- Treat cost optimization as an operating practice using capacity metrics, refresh optimization, workload consolidation, and storage lifecycle management.

## Activities

- Cost analysis
- Capacity and licensing optimization
- Storage optimization
- Migration cost estimate
- Operational support estimate
- Business benefits analysis
- ROI scenario modeling
- Cost governance model

## Deliverables

- Executive Business Case
- ROI Model
- Cost Model
- Capacity and Licensing Recommendation
- Optimization Backlog
- Benefits Realization Plan

## Exit Criteria

- Funding model and cost ownership are agreed.
- Initial capacity and licensing strategy is approved.
- ROI assumptions are documented and traceable to measured or agreed inputs.

---

# Phase 5 - Landing Zone and Foundation

## Objectives

Establish the secure, governed, and repeatable Microsoft Fabric foundation required before production workloads are onboarded.

## Microsoft Best Practices

- Configure tenant settings intentionally and restrict high-impact settings to approved security groups.
- Use Microsoft Entra ID groups for Fabric admins, capacity admins, workspace admins, contributors, members, and viewers.
- Assign workspaces to Fabric capacity based on environment, workload criticality, domain ownership, and performance needs.
- Standardize workspace naming, ownership, descriptions, domains, deployment stages, endorsement, and lifecycle status.
- Enable Git integration and deployment pipelines where supported for controlled promotion.
- Use approved connection, credential, gateway, and secret-management patterns.
- Apply sensitivity labels, data loss prevention expectations, and audit controls for governed data products.
- Configure monitoring for capacity metrics, refresh failures, pipeline failures, access changes, and production deployment events.
- Document operational runbooks, support ownership, escalation paths, and rollback procedures.

## Activities

- Fabric capacity configuration
- Tenant setting review and configuration
- Identity and access setup
- Workspace and domain provisioning
- Network and data source connectivity setup
- Governance policy implementation
- Git integration and deployment pipeline setup
- Monitoring and alerting setup
- Operational runbook creation

## Deliverables

- Landing Zone
- Governance Framework
- Workspace Standards
- Identity and Access Matrix
- Deployment Pipeline Configuration
- Monitoring and Operations Runbook
- Security and Compliance Baseline

## Exit Criteria

- Foundational access is group-based and reviewed.
- Workspaces and capacity assignments follow approved standards.
- Monitoring, deployment, and support controls are ready for PoC workloads.

---

# Phase 6 - Proof of Concept (PoC)

## Objectives

Validate the Microsoft Fabric solution technically and operationally before business adoption and production rollout.

## Microsoft Best Practices

- Select a representative workload with real data patterns, security requirements, refresh expectations, and business users.
- Deploy through the approved dev/test/prod promotion path rather than making production changes manually.
- Validate OneLake storage patterns, shortcuts, lakehouse or warehouse design, pipeline orchestration, semantic model performance, and report usability.
- Test workspace access using Microsoft Entra ID groups and verify least-privilege access for owners, contributors, and consumers.
- Measure capacity utilization, refresh duration, pipeline runtime, query performance, and throttling indicators.
- Validate sensitivity labels, audit events, data lineage, data quality checks, rollback, and operational support handoff.
- Update cost assumptions based on measured PoC consumption.

## Activities

- Deploy Fabric PoC foundation
- Build lakehouse and/or warehouse assets
- Connect representative sample data
- Create data pipelines
- Publish semantic models and Power BI reports
- Validate OneLake architecture
- Configure Git integration and deployment pipelines
- Run performance testing
- Run security and access testing
- Run operational monitoring tests
- Update cost and ROI assumptions

## Exit Criteria

- Performance validated
- Security approved
- Governance controls verified
- Deployment promotion path validated
- Monitoring and support model validated
- Cost assumptions updated with measured usage
- Business sign-off received

## Deliverables

- PoC Report
- Lessons Learned
- Go / No-Go Recommendation
- Performance Test Results
- Security Test Results
- Updated Cost Model
- Production Rollout Backlog

---

# Cross-Phase Controls

## Governance

- Use named owners for every workspace, data product, and production report.
- Require pull request review for deployment specs, production reports, and security-impacting changes.
- Maintain a decision log for architecture, governance, cost, and security decisions.

## Security

- Use Microsoft Entra ID groups rather than direct user assignments.
- Apply least privilege across tenant, capacity, workspace, item, and data-source access.
- Keep secrets out of Git and use approved secret stores or credential management patterns.

## Deployment

- Treat deployment specs, workspace standards, and environment parameters as version-controlled assets.
- Promote changes through dev, test, and production with validation gates.
- Keep rollback steps and release evidence for production deployments.

## Operations

- Monitor capacity, refreshes, pipelines, security events, and user activity.
- Review access, ownership, and inactive assets regularly.
- Revisit capacity sizing and cost optimization after each major workload onboarding.
