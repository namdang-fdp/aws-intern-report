---
title: "Week 7 Worklog"
date: 2024-10-21
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Goals

-   **Strategic Consolidation:** Execute a comprehensive synthesis of core AWS competencies in preparation for the mid-term assessment.
-   **Exam Simulation:** Engage in rigorous hands-on labs and scenario-based testing via **AWS Builders** and **AWSboy** platforms to align with examination standards.
-   **Architectural Systematization:** Structured review of fundamental service interdependencies including EC2, S3, VPC, IAM, RDS, Lambda, and DynamoDB.

---

### Weekly Task Execution

| Day       | Activity                                                                                                                                                                                                                                                                                                                                   | Start Date | Completion Date | Resources            |
| :-------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :------------------- |
| Monday    | - **Compute Architecture Synthesis:** Deep dive into EC2 lifecycles and Lambda event-driven models. <br> - **Practical Simulation:** Execute end-to-end lifecycle management of **EC2 Instances** (Launch to Termination). <br> - **Serverless Review:** Analyze Lambda execution environments and trigger logic.                          | 22/10/2024 | 22/10/2024      | AWS Builders, AWSboy |
| Tuesday   | - **Storage Hierarchy Analysis:** Compare and contrast Block (EBS), Object (S3), and File (EFS) storage paradigms. <br> - **Hands-on Implementation:** Configure S3 tiering strategies (Standard, IA, Glacier) and EBS volume types. <br> - **Security Controls:** Enforce granular S3 bucket policies and ACLs.                           | 23/10/2024 | 23/10/2024      | AWS Builders, AWSboy |
| Wednesday | - **Network Topology Engineering:** Dissect VPC internals (Subnetting, Route Tables, IGW, Security Layers). <br> - **Scenario Testing:** Distinguish between Security Group (Stateful) and NACL (Stateless) configurations. <br> - **Connectivity:** Review inter-network communication via VPC Peering and Transit Gateway.               | 24/10/2024 | 24/10/2024      | AWS Builders, AWSboy |
| Thursday  | - **Persistence & Governance:** Solidify knowledge of Database consistency models (RDS vs. DynamoDB) and Identity Governance (IAM). <br> - **Identity Management:** Architect secure **IAM Policies**, **Roles**, and **User** hierarchies. <br> - **Database Config:** Practice DynamoDB capacity planning and RDS instance provisioning. | 25/10/2024 | 25/10/2024      | AWS Builders, AWSboy |
| Friday    | - **Exam Readiness Assessment:** Undertake **comprehensive mock exams** on simulation platforms. <br> - **Gap Analysis:** Identify and remediate weak knowledge areas revealed during testing. <br> - **Knowledge Artifacts:** Compile condensed summary notes for rapid pre-exam reference.                                               | 26/10/2024 | 26/10/2024      | AWS Builders, AWSboy |

---

### Week 7 Outcomes

**Holistic Competency Achieved:**

-   **Service Mastery:** Achieved a holistic understanding of the AWS Cloud Adoption Framework pillars: Compute, Storage, Networking, Database, and Security.
-   **Scenario Proficiency:** Successfully navigated complex lab scenarios and multiple-choice constraints on **AWS Builders** and **AWSboy**.
-   **Operational Fluency:**
    -   **Compute:** Mastered EC2 parameterization (Instance Families, AMI selection, EBS optimization).
    -   **Storage:** Internalized S3 object management and lifecycle economics.
-   **Network Depth:** Attained clarity on **VPC** architectural components (Public/Private isolation, Routing logic, Defense-in-depth security).
-   **Exam Readiness:** Reached a high level of confidence through iterative testing and review.
-   **Knowledge Base:** Created a centralized repository of study notes covering all major service categories.
-   **Remediation:** Proactively addressed and resolved knowledge gaps identified during practice sessions.

**Core Insights:**

-   **Security Layering:** Security Groups act as stateful firewalls (automatic return traffic), whereas NACLs are stateless (requiring explicit bidirectional rules).
-   **Workload Optimization:** EC2 instance families are purpose-built for specific bottlenecks (Compute, Memory, Storage, or GPU).
-   **Storage Economics:** S3 storage classes are designed to balance retrieval costs against access frequency requirements.
-   **IAM Logic:** Policy evaluation follows an "Implicit Deny" default, where the most restrictive policy (Explicit Deny) always wins.
-   **Routing Precision:** VPC routing decisions rely on the "Longest Prefix Match" principle to determine traffic paths.
