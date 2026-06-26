# Microsoft Fabric Deployment Cost Model

## Purpose

This model estimates the cost of deploying Microsoft Fabric across assessment, landing zone, proof of concept, and production rollout activities. Use it to compare capacity options, implementation effort, licensing needs, storage growth, and operational run costs.

## Cost Categories

| Category | Description | Cost Driver |
| --- | --- | --- |
| Fabric Capacity | Reserved or pay-as-you-go Fabric capacity for development, test, and production | Capacity SKU, hours per month, reservation discount |
| Power BI Licensing | User licensing for report consumers, creators, admins, and developers | User count and license type |
| OneLake Storage | Lakehouse, warehouse, shortcuts, retained files, and backup/retention data | Stored TB per month |
| Data Integration | Data Factory pipelines, data movement, gateways, and orchestration | Pipeline count, runtime, data volume |
| Data Engineering | Spark notebooks, lakehouse transformations, batch processing | Compute usage and execution frequency |
| Security and Governance | Purview, sensitivity labels, private networking, audit, monitoring | Tooling, setup effort, operational effort |
| Migration and Implementation | Architecture, build, test, deployment, documentation, enablement | Role rates and estimated days |
| Operations | Platform administration, monitoring, incident response, enhancements | Monthly support hours |

## Key Assumptions

| Assumption | Baseline Value | Notes |
| --- | ---: | --- |
| Currency | USD | Change if your commercial model uses another currency |
| Monthly hours for always-on capacity | 730 | Standard monthly planning estimate |
| Environments | Dev, Test, Prod | Adjust for sandbox or DR environments |
| Reservation discount | 0% | Replace with contracted discount if applicable |
| Storage growth | 20% annually | Update after current-state assessment |
| Implementation duration | 12 weeks | Covers landing zone and PoC baseline |
| Support model | Business hours | Add 24x7 uplift if required |

## Monthly Run Cost Formula

```text
Monthly Run Cost = Fabric Capacity Cost
                 + Power BI License Cost
                 + OneLake Storage Cost
                 + Data Integration Cost
                 + Monitoring and Governance Cost
                 + Operations Support Cost
```

## One-Time Deployment Cost Formula

```text
One-Time Deployment Cost = Discovery and Assessment
                         + Architecture and Design
                         + Landing Zone Build
                         + PoC Build
                         + Migration and Testing
                         + Documentation and Enablement
```

## Total Cost of Service Deployed

Use this section to calculate the total cost of the deployed Fabric service after the solution is live. The total should include both the one-time deployment investment and the recurring run cost for the selected operating period.

```text
Total Cost of Service Deployed = One-Time Deployment Cost
                               + (Monthly Run Cost x Number of Operating Months)
                               + Contingency
```

| TCO View | Formula | When To Use |
| --- | --- | --- |
| First-Year Cost | One-Time Deployment Cost + (Monthly Run Cost x 12) + Contingency | Executive business case and year-one funding approval |
| Three-Year Cost | One-Time Deployment Cost + (Monthly Run Cost x 36) + Contingency | Standard platform investment comparison |
| Five-Year Cost | One-Time Deployment Cost + (Monthly Run Cost x 60) + Contingency | Long-range enterprise architecture and sourcing decisions |

## Service Cost Summary Template

| Cost Component | One-Time Cost | Monthly Cost | 12-Month Total | 36-Month Total | 60-Month Total | Notes |
| --- | ---: | ---: | ---: | ---: | ---: | --- |
| Fabric capacity | 0 | TBD | TBD | TBD | TBD | Include dev, test, and prod capacity assumptions |
| Power BI licensing | 0 | TBD | TBD | TBD | TBD | Include creators, admins, and consumers where applicable |
| OneLake storage | 0 | TBD | TBD | TBD | TBD | Include expected annual growth and retention |
| Data integration and engineering | 0 | TBD | TBD | TBD | TBD | Include pipelines, notebooks, orchestration, and refresh workload |
| Security, governance, and monitoring | TBD | TBD | TBD | TBD | TBD | Include setup, audit, compliance, and operations tooling |
| Migration and implementation | TBD | 0 | TBD | TBD | TBD | Include assessment, design, build, testing, and handover |
| Operations support | 0 | TBD | TBD | TBD | TBD | Include platform administration and incident response |
| Contingency | TBD | TBD | TBD | TBD | TBD | Recommended for unknown workload growth or migration risk |
| Total service cost | TBD | TBD | TBD | TBD | TBD | Sum all service cost components |

## Service Cost Reporting Guidance

- Report total service cost separately from business benefit and ROI so stakeholders can see the gross platform investment clearly.
- Separate production run cost from non-production run cost when capacity scheduling or smaller dev/test SKUs are used.
- Show assumptions for capacity SKU, operating hours, reservation discount, storage growth, license counts, and support coverage.
- Include a contingency line for migration uncertainty, workload growth, and performance tuning.
- Recalculate total service cost after PoC validation using measured capacity, refresh, storage, and pipeline usage.
- Review actual spend monthly after production launch and compare it against the approved cost model.

## Baseline Estimate Template

| Cost Item | Quantity | Unit Cost | Frequency | Estimated Cost | Owner | Notes |
| --- | ---: | ---: | --- | ---: | --- | --- |
| Fabric capacity - Dev | 1 | TBD | Monthly | TBD | Platform | Select SKU after capacity sizing |
| Fabric capacity - Test | 1 | TBD | Monthly | TBD | Platform | May be scheduled during business hours |
| Fabric capacity - Prod | 1 | TBD | Monthly | TBD | Platform | Consider reserved capacity |
| Power BI Pro licenses | TBD | TBD | Monthly | TBD | Business | Report creators and workspace contributors |
| Power BI Premium Per User | TBD | TBD | Monthly | TBD | Business | Only if required by feature model |
| OneLake storage | TBD TB | TBD | Monthly | TBD | Data Platform | Include raw, curated, and semantic layers |
| Data pipeline execution | TBD | TBD | Monthly | TBD | Data Engineering | Based on refresh frequency and volume |
| Gateway or network components | TBD | TBD | Monthly | TBD | Infrastructure | Required for private or on-prem connectivity |
| Monitoring and logging | TBD | TBD | Monthly | TBD | Operations | Include alerting and audit retention |
| Assessment workshops | TBD days | TBD | One-time | TBD | Delivery | Current state and requirements |
| Architecture and design | TBD days | TBD | One-time | TBD | Delivery | Target architecture and governance |
| Landing zone implementation | TBD days | TBD | One-time | TBD | Delivery | Capacity, identity, networking, workspaces |
| PoC implementation | TBD days | TBD | One-time | TBD | Delivery | Lakehouse, pipelines, reports, validation |
| Testing and sign-off | TBD days | TBD | One-time | TBD | Delivery | Performance, security, business validation |
| Documentation and handover | TBD days | TBD | One-time | TBD | Delivery | Runbooks, design docs, training |

## Sizing Inputs To Collect

| Input | Why It Matters |
| --- | --- |
| Number of workspaces | Drives governance, deployment automation, and administration effort |
| Number of report consumers | Drives Power BI license and capacity strategy |
| Number of report authors | Drives Pro/PPU licensing and enablement effort |
| Current Power BI dataset size | Helps size Fabric capacity and migration effort |
| Synapse workloads | Identifies warehouse, Spark, and pipeline migration scope |
| Data refresh frequency | Drives capacity, pipeline, and performance requirements |
| Data volume ingested per day | Drives storage, integration, and compute sizing |
| Security zones and data classifications | Drives governance, sensitivity labels, access design, and audit needs |
| Required RPO/RTO | Drives resiliency, backup, and support cost |
| Environments and deployment rings | Drives capacity, Dev/Test/Prod, CI/CD, and operations cost |

## Cost Optimization Levers

- Use capacity scheduling for non-production environments.
- Start PoC on a smaller capacity and resize after measured workloads.
- Separate development, test, and production only where governance requires it.
- Use OneLake shortcuts where they reduce duplicate storage.
- Apply lifecycle and retention policies to raw and staging data.
- Consolidate low-value refresh schedules.
- Use deployment pipelines and Git integration to reduce manual release effort.
- Review workspace ownership and inactive assets monthly.

## Review Cadence

| Milestone | Cost Model Action |
| --- | --- |
| Phase 2 - Current State Assessment | Replace assumptions with actual inventory, usage, and capacity data |
| Phase 3 - Architecture and Design | Confirm target capacity model and environment strategy |
| Phase 4 - Business Case and ROI | Finalize cost baseline, benefits, and ROI scenarios |
| Phase 5 - Landing Zone and Foundation | Validate landing zone implementation cost and run cost |
| Phase 6 - PoC | Measure real workload usage and update production forecast |

## ROI Considerations

| Benefit Area | Measurement Approach |
| --- | --- |
| Platform consolidation | Retired tools, reduced duplicate storage, reduced admin overhead |
| Faster analytics delivery | Cycle time reduction for new datasets, reports, and pipelines |
| Improved governance | Reduced audit effort, improved lineage, better access control |
| Operational efficiency | Fewer manual deployments, fewer refresh failures, faster support response |
| Business value | Revenue enablement, decision speed, compliance outcomes, risk reduction |
