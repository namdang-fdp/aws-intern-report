---
title: "Week 4 Worklog"
date: 2025-09-29
weight: 4
chapter: false
pre: "<b>1.4. </b>"
---

### Week 4 Goals

-   Synchronize technical proficiency with team momentum regarding AWS ecosystems.
-   Achieve architectural mastery of AWS Transit Gateway for centralized network management.
-   Augment core competency in Amazon EC2 and scalable compute services.
-   Internalize Git version control workflows to enhance team synergy.
-   **Workshop Initialization:** Provision the foundational VPC & Network infrastructure for the Bandup IELTS project.

### Weekly Task Execution

| Day | Activity                                                                                                                                                                                                                                                                                                                       | Start Date | Completion Date | Reference Material                                                                   |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ------------------------------------------------------------------------------------ |
| 2   | - **Network Architecture:** Deep dive into AWS Transit Gateway concepts, deployment workflows, and prerequisites.<br>- **Comparative Analysis:** Evaluate architectural differences between VPC Peering and Transit Gateway.<br>- **Completion:** Finished module _Centralized Network Management with AWS Transit Gateway_.   | 29/09/2025 | 30/09/2025      | [AWS Transit Gateway](https://aws.amazon.com/transit-gateway/)                       |
| 3   | - **Compute Advanced Study:** Examine Amazon EC2 internals via Module 3 lectures.<br>- **Elasticity Implementation:** Master automated resource provisioning using EC2 Auto Scaling.<br>- **Completion:** Finished module _Scaling Applications with EC2 Auto Scaling_.                                                        | 01/10/2025 | 02/10/2025      | [FCJ Playlist](https://youtube.com/playlist?list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i) |
| 4   | - **Version Control:** Standardize collaborative workflows using Git operations (commit, push, pull).<br>- **Lightweight Compute:** Evaluate Amazon Lightsail for streamlined VPS requirements.<br>- **Completion:** Finished module _Simplified Computing with Amazon Lightsail_.                                             | 03/10/2025 | 04/10/2025      | [Git Tutorial](https://www.youtube.com/watch?v=8O14qT3jdq0)                          |
| 5   | - **Project Governance:** Orchestrate task delegation and finalize strategies for the project proposal.<br>- **Migration Strategy:** Analyze workload mobility using AWS VM Import/Export.<br>- **Workshop Execution:** Architect and provision the initial VPC environment (CIDR `10.0.0.0/16`) including DNS configurations. | 05/10/2025 | 06/10/2025      | Team Meeting, [Workshop 5.3](5-Workshop/5.3-VPC-Network/)                            |

### AWS Skill Builder Curriculum Completed

| Course                                                  | Category    | Status |
| ------------------------------------------------------- | ----------- | ------ |
| Centralized Network Management with AWS Transit Gateway | Networking  | ✅     |
| Scaling Applications with EC2 Auto Scaling              | Compute     | ✅     |
| Simplified Computing with Amazon Lightsail              | Compute     | ✅     |
| Container Deployment with Amazon Lightsail Containers   | Containers  | ✅     |
| VM Migration with AWS VM Import/Export                  | Migration   | ✅     |
| Database Migration with AWS DMS and SCT                 | Migration   | ✅     |
| Disaster Recovery with AWS Elastic Disaster Recovery    | Reliability | ✅     |
| Monitoring with Amazon CloudWatch                       | Operations  | ✅     |

### Week 4 Outcomes

**Technical Proficiency Gained:**

_AWS Transit Gateway Architecture:_

-   Engineered a centralized network hub using Transit Gateway.
-   Identified strategic differentiators compared to VPC Peering:
    -   Capability to support complex **hub-and-spoke topologies**.
    -   Enablement of **transitive routing** between interconnected networks.
    -   Operational simplicity when scaling network connections.
    -   Seamless integration with VPN and Direct Connect.
-   Acquired expertise in managing Transit Gateway route tables.

_Amazon EC2 & Compute Elasticity:_

-   Attained deep-dive proficiency in EC2 core features:
    -   **Elasticity:** Leveraging auto-scaling mechanics for dynamic load adaptation.
    -   **Workload Optimization:** Selecting appropriate instance families for specific tasks.
    -   **Cost Efficiency:** Utilizing On-Demand, Reserved, and Spot pricing models effectively.
-   Mastered **EC2 Auto Scaling** for automated fleet management.
-   Understood the distinctions of **Instance Store** as high-performance ephemeral storage.
-   Evaluated **Amazon Lightsail** for rapid deployment of small-scale applications and containers.

_Migration & Resilience:_

-   Analyzed **AWS Application Migration Service (MGN)** for lift-and-shift operations.
-   Explored **VM Import/Export** methodologies for hybrid cloud mobility.
-   Reviewed database transition strategies using **DMS** and **SCT**.
-   Formulated business continuity plans using **AWS Elastic Disaster Recovery**.

_DevOps & Observability:_

-   Solidified **Git** version control practices for distributed team collaboration.
-   Grasped **Amazon CloudWatch** fundamentals for resource monitoring and observability.

**Collaborative Progress:**

-   Led the brainstorming session and finalized the roadmap for the project proposal.
-   Transitioned the team into the implementation phase with high readiness.
-   Defined and assigned granular roles and responsibilities to team members.

**Workshop Progress - VPC & Network Infrastructure:**

-   **Core Infrastructure:** Provisioned the primary VPC with CIDR `10.0.0.0/16` in the `ap-southeast-1` region.
-   **Network Segmentation:** Implemented a multi-tier subnet architecture:
    -   Public Tier: `10.0.1.0/24`, `10.0.2.0/24`.
    -   Application Tier (Private): `10.0.11.0/24`, `10.0.12.0/24`.
    -   Database Tier (Private): `10.0.21.0/24`, `10.0.22.0/24`.
-   **Connectivity:** Established Internet Gateway attachments for public ingress/egress.
-   **Routing Logic:** Configured route tables to strictly control traffic flow between tiers.
-   **Security Layer:** Initiated Security Group definitions to enforce micro-segmentation.

**Core Insights:**

-   **Transit Gateway** serves as the pivotal backbone for scalable, multi-VPC routing architectures.
-   **EC2 Auto Scaling** is non-negotiable for ensuring high availability and cost optimization under fluctuating loads.
-   **Migration Services** offer diverse pathways (Rehost, Replatform) to accelerate cloud adoption.
-   **VPC Design** with strict Public/Private isolation is the foundation of secure cloud infrastructure.
-   **Multi-AZ Architecture** acts as the first line of defense for network resilience and fault tolerance.
