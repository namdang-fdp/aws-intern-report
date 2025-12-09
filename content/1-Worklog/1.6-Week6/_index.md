---
title: "Week 6 Worklog"
date: 2025-10-14
weight: 6
chapter: false
pre: "<b>1.6. </b>"
---

### Week 6 Goals

-   Attain comprehensive mastery of AWS Object and Hybrid Storage hierarchies and their architectural use cases.
-   Fortify backend development proficiency via Python practical application.
-   Crystallize the project's infrastructure topology and finalize component relationships.
-   Acquire cutting-edge insights into Generative AI-driven DevSecOps via industry webinars.
-   **Workshop Finalization:** Provision the **Persistence Layer** (Database & Storage) and configure static asset delivery.

### Weekly Task Execution

| Day | Activity                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | Start Date | Completion Date | Reference Material                                                                                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ------------------------------------------------------------------------------------------------------------- |
| 2   | - **Object Storage Deep Dive:** Dissect Amazon S3 bucket architecture, 11-9s durability guarantees, and static hosting mechanisms.<br>- **Tiering Strategy:** Analyze S3 Storage Classes (Standard, IA) and Amazon Glacier for cold data archival.<br>- **Completion:** Finished module _Static Website Hosting with Amazon S3_.                                                                                                                                                                             | 14/10/2025 | 15/10/2025      | [AWS S3 Documentation](https://aws.amazon.com/s3/)                                                            |
| 3   | - **Hybrid Integration:** Evaluate AWS Storage Gateway modalities (File, Volume, Tape) for bridging on-prem and cloud.<br>- **Cost Governance:** Architect Object Lifecycle Management policies.<br>- **Algorithmic Practice:** Refine Python data structure manipulation and error handling logic.<br>- **Industry Engagement:** Attended webinar _"Reinventing DevSecOps with AWS Generative AI"_ featuring speaker Hoang Kha.                                                                             | 16/10/2025 | 17/10/2025      | [AWS Storage Gateway](https://aws.amazon.com/storagegateway/)<br>[AWS Events](https://aws.amazon.com/events/) |
| 4   | - **Resiliency Engineering:** Internalize RTO/RPO metrics and Backup & Restore methodologies.<br>- **Data Protection:** Implement centralized governance using AWS Backup.<br>- **Practical Implementation:** Provision S3 buckets, deploy static sites, and validatelifecycle transitions.<br>- **DevSecOps Research:** Investigate CI/CD pipelines, SAST/DAST tooling, and IaC security.<br>- **Workshop Execution:** Provision production-grade RDS PostgreSQL (Multi-AZ) and ElastiCache Redis clusters. | 18/10/2025 | 19/10/2025      | [AWS Backup](https://aws.amazon.com/backup/), [Workshop 5.6](5-Workshop/5.6-Database-Storage/)                |
| 5   | - **Architectural Freeze:** Finalize the detailed infrastructure diagram mapping all component interactions.<br>- **Code Governance:** Refactor the repository structure to mirror the finalized architecture.<br>- **Standardization:** Lock in the technology stack and frameworks for team consistency.<br>- **AI-Assisted Development:** Evaluate **Amazon Q Developer** for code generation, unit testing, and vulnerability remediation.                                                               | 20/10/2025 | 21/10/2025      | [Amazon Q Developer](https://aws.amazon.com/q/developer/)                                                     |

### AWS Skill Builder Curriculum Completed

| Course                                  | Category    | Status |
| --------------------------------------- | ----------- | ------ |
| Static Website Hosting with Amazon S3   | Storage     | ✅     |
| Data Protection with AWS Backup         | Reliability | ✅     |
| Content Delivery with Amazon CloudFront | Networking  | ✅     |

### Week 6 Outcomes

**Technical Proficiency Gained:**

_Storage Ecosystem Proficiency:_

-   **S3 Architecture:** Achieved deep understanding of bucket mechanics, durability guarantees (99.999999999%), and static hosting capabilities.
-   **Data Tiering:** Mastered the application of Storage Classes (Standard, Standard-IA, Glacier) based on access frequency patterns.
-   **Hybrid Interfaces:** Learned integration patterns for AWS Storage Gateway to extend cloud storage to on-premises environments.
-   **Automated Optimization:** Configured Object Lifecycle Management for automated data transition and cost reduction.

_Business Continuity & Resilience:_

-   **DR Fundamentals:** Grasped critical metrics including **RTO** (Recovery Time Objective) and **RPO** (Recovery Point Objective).
-   **Unified Backup:** Utilized **AWS Backup** for policy-based backup management across supported AWS services.
-   **Restoration Strategy:** Formulated strategies for data recovery to ensure business continuity.

_Development & Operational Rigor:_

-   **Python Fluency:** Sharpened Python programming skills through targeted data structure and error handling exercises.
-   **Practical Deployment:** Successfully provisioned S3 resources, configured public access blocks, and validated hosting logic.
-   **Infrastructure Governance:** Restructured the codebase directory hierarchy to align with architectural standards.

_DevSecOps & Generative AI Integration:_

-   **Industry Insight:** Gained actionable knowledge from the webinar _"Reinventing DevSecOps with AWS Generative AI"_ (Oct 16, 2025).
-   **Security Pipeline:** Understood the integration of security into the SDLC using Jenkins (CI/CD), SonarQube (SAST), OWASP ZAP (DAST), and Terraform (IaC).
-   **AI Tooling:** Explored **Amazon Q Developer** as an intelligent assistant for accelerating code delivery and proactively scanning for vulnerabilities.

**Workshop Progress - Persistence Layer Deployment:**

-   **Relational Database:** Deployed **RDS PostgreSQL** with Multi-AZ configuration in private subnets to guarantee High Availability and automatic failover.
-   **In-Memory Caching:** Provisioned **ElastiCache Redis** cluster to optimize session management and sub-millisecond read performance.
-   **Object Storage:** Established S3 buckets for diverse workloads (static assets, user uploads, logs).
-   **Cost Automation:** Implemented S3 lifecycle policies to automatically transition aging data to Glacier.
-   **Integration:** Finalized database connection strings and caching endpoints for application consumption.
-   **Data Protection:** Enrolled critical persistence resources into AWS Backup plans.

**Core Insights:**

-   **S3** acts as the omnipresent storage layer; selecting the correct Storage Class is the primary lever for cost efficiency.
-   **Lifecycle Policies** turn manual data management into an automated, "set-and-forget" cost-saving mechanism.
-   **DevSecOps** represents a "Shift-Left" culture where security is baked into the code and pipeline, not audited at the end.
-   **RDS Multi-AZ** is non-negotiable for production workloads requiring minimal downtime.
-   **Caching (Redis)** is the most effective method to decouple database load from read-heavy application traffic.
-   **Private Subnet Placement** for databases enforces a strict security posture by eliminating direct internet exposure.
