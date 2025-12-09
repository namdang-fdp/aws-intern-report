---
title: "Week 5 Worklog"
date: 2025-10-07
weight: 5
chapter: false
pre: "<b>1.5. </b>"
---

### Week 5 Goals

-   Audit and remediate financial anomalies to stabilize the AWS account budget.
-   Architect and segment the infrastructure topology for the core project.
-   Initiate codebase scaffolding and delineate team roles and responsibilities.
-   Leverage the AWS Skill Builder ecosystem to advance proficiency in resource optimization.
-   **Workshop Finalization:** Solidify VPC Network logic and commence the provisioning of the **Data Persistence Layer** (Database & Storage).

### Weekly Task Execution

| Day | Activity                                                                                                                                                                                                                                                                                                                                                                            | Start Date | Completion Date | Reference Material                                                                                             |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | -------------------------------------------------------------------------------------------------------------- |
| 2   | - **Financial Forensics:** Analyze billing granularities to identify root causes of cost spikes.<br>- **Governance:** Establish quotas and monitoring.<br>- **Completion:** Finished modules _Cost and Usage Management_ and _Managing Quotas with Service Quotas_.                                                                                                                 | 07/10/2025 | 08/10/2025      | [AWS Cost Explorer](https://aws.amazon.com/aws-cost-management/aws-cost-explorer/)                             |
| 3   | - **Infrastructure Design:** Draft the high-level architecture diagrams and partitioning strategies.<br>- **Standardization:** Propose architectural blueprints for team adoption.<br>- **Completion:** Finished module _Building Highly Available Web Applications_.<br>- **Workshop Execution:** Deploy NAT Gateways for secure egress and finalize Security Group parameters.    | 09/10/2025 | 10/10/2025      | [FCJ Community](https://www.facebook.com/groups/awsstudygroupfcj), [Workshop 5.3](5-Workshop/5.3-VPC-Network/) |
| 4   | - **Project Scaffolding:** Construct the initial code skeleton and configuration manifests.<br>- **IDE Configuration:** Integrate AWS tools into the local development environment.<br>- **Completion:** Finished module _Development Environment with AWS Toolkit for VS Code_.<br>- **Workshop Execution:** Strategize RDS PostgreSQL and ElastiCache Redis implementation plans. | 11/10/2025 | 13/10/2025      | VS Code + AWS Toolkit, [Workshop 5.6](5-Workshop/5.6-Database-Storage/)                                        |
| 5   | - **Continuous Learning:** Onboard to AWS Skill Builder and curate a learning path.<br>- **Optimization Strategy:** Master rightsizing methodologies for compute resources.<br>- **Completion:** Finished module _Right-Sizing with EC2 Resource Optimization_.                                                                                                                     | 11/10/2025 | 12/10/2025      | [AWS Skill Builder](https://skillbuilder.aws/)                                                                 |

### AWS Skill Builder Curriculum Completed

| Course                                               | Category          | Status |
| ---------------------------------------------------- | ----------------- | ------ |
| Cost and Usage Management                            | Cost Optimization | ✅     |
| Managing Quotas with Service Quotas                  | Operations        | ✅     |
| Billing Console Delegation                           | Cost Management   | ✅     |
| Right-Sizing with EC2 Resource Optimization          | Cost Optimization | ✅     |
| Development Environment with AWS Toolkit for VS Code | Development       | ✅     |
| Building Highly Available Web Applications           | Architecture      | ✅     |
| Database Essentials with Amazon RDS                  | Database          | ✅     |
| NoSQL Database Essentials with Amazon DynamoDB       | Database          | ✅     |
| In-Memory Caching with Amazon ElastiCache            | Database          | ✅     |
| Command Line Operations with AWS CLI                 | Operations        | ✅     |

### Week 5 Outcomes

**Technical Proficiency Gained:**

_Cost Optimization & Governance:_

-   **Diagnosed financial leakage vectors:**
    -   Orphaned EBS volumes and unattached Elastic IPs post-termination.
    -   Loose IAM permission boundaries leading to unmonitored provisioning.
    -   Zombie resources persisting in non-active regions.
-   **Internalized financial governance frameworks:**
    -   **AWS Budgets:** Implemented proactive thresholds for cost alerting.
    -   **Cost Explorer:** Mastered granular analysis of spending trends.
    -   **Service Quotas:** Configured guardrails to prevent accidental over-provisioning.
    -   **Billing Delegation:** Decentralized cost visibility to relevant stakeholders.

_Architectural Engineering:_

-   **Infrastructure Blueprinting:** Finalized the logical topology for the project's infrastructure.
-   **Reference Architectures:** Developed standardized templates to ensure consistency.
-   **High Availability (HA) Enforcement:**
    -   Architected Multi-AZ redundancy strategies.
    -   Designed robust Load Balancing mechanisms.
    -   Defined Database Replication patterns for fault tolerance.

_Developer Experience (DX):_

-   **IDE Integration:** Seamlessly integrated AWS Toolkit for VS Code to accelerate workflows.
-   **CLI Mastery:** Achieved fluency in command-line resource manipulation via AWS CLI.
-   **Project Scaffolding:** Engineered a scalable boilerplate with robust initial configurations.

_Data Persistence Strategy:_

-   **Relational:** Validated **Amazon RDS** for structured, transactional data requirements.
-   **NoSQL:** Evaluated **DynamoDB** for high-throughput, low-latency scenarios.
-   **Caching:** Selected **ElastiCache** (Redis) to offload database read pressure.

**Project Momentum:**

-   **Skill Acquisition:** Fully onboarded to the AWS Skill Builder ecosystem for continuous upskilling.
-   **Blueprint Freeze:** Infrastructure architecture has been reviewed, finalized, and documented.
-   **Ready-to-Code:** Development environment is fully provisioned and optimized for collaboration.

**Workshop Progress - Network & Data Layer:**

-   **Secure Egress:** Executed NAT Gateway deployment in public subnets to facilitate secure internet access for private workloads.
-   **Zero-Trust Networking:** Configured granular Security Groups for ALB, ECS, RDS, and ElastiCache tiers, enforcing strict least-privilege access.
-   **Routing Logic:** Defined precise route tables (IGW for Public, NAT GW for Private).
-   **Database Architecture:** Architected the RDS PostgreSQL layer with Multi-AZ for production-grade availability.
-   **Caching Layer:** Planned the ElastiCache Redis cluster for session state management.
-   **Object Storage:** Configured S3 buckets to handle static assets and document archival.

**Core Insights:**

-   **Financial Hygiene** is predicated on constant observability via Cost Explorer.
-   **Instance Right-Sizing** is a high-impact lever for reducing OpEx (up to 30-50%).
-   **Resiliency** is not accidental; it is engineered through deliberate Multi-AZ planning.
-   **Developer Productivity** is significantly amplified by proper tooling (AWS Toolkit/CLI).
-   **Polyglot Persistence** (using the right DB for the right job) is critical for performance.
-   **Security Groups** function as the primary, stateful firewall mechanism for defense-in-depth.
