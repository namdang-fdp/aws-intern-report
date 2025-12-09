---
title: "Worklog Week 11"
date: 2024-11-18
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Goals

-   **Strategic Consultation:** Leverage expert insights from **AWS Cloud Mastery Series #2** to resolve complex authorization and AI workflow challenges.
-   **Frontend Modernization:** Execute architectural standardization of the Frontend codebase to enhance stability and maintainability.
-   **Infrastructure Modularization:** Orchestrate a **Multi-Stack** topology to decouple resources and accelerate the Serverless deployment pipeline.
-   **AI Integration:** Synthesize CRUD logic with AI-driven pipelines (Image Processing/Generative AI) utilizing asynchronous patterns.
-   **Deployment Stabilization:** Permanently remediate persistent deployment bottlenecks, specifically Cross-Origin Resource Sharing (CORS) anomalies.
-   **Workshop Execution:** Provision the **AI Service Architecture**, enforce Security/IAM governance, and establish Monitoring/Observability.

---

### Weekly Task Execution

| Day | Activity                                                                                                                                                                                                                                                                                                                                                           | Start Date | Completion Date | Resources                                                                      |
| :-- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :----------------------------------------------------------------------------- |
| Sun | - **Advanced Technical Inquiry:** Engage with experts in **AWS Cloud Mastery Series #2** regarding granular authorization pitfalls and optimal AI workflow orchestration.                                                                                                                                                                                          | 17/11/2024 | 17/11/2024      | Mentor, AWS Cloud Mastery Series                                               |
| Mon | - **Codebase Governance:** Convene team synchronization to homologate the Frontend structure. <br> - **Architecture Analysis:** Formulate a strategy to decompose the monolithic `template.yaml` into granular, domain-specific Stacks to optimize `sam deploy` latency.                                                                                           | 18/11/2024 | 18/11/2024      | Serverless Architecture Docs                                                   |
| Tue | - **Stack Decomposition:** Provision isolated CloudFormation Stacks (e.g., API Backend Stack, Frontend Hosting Stack). <br> - **AI Logic Synthesis:** Merge CRUD operations with AI processing triggers (Rekognition/S3 events). <br> - **Workshop Execution:** Architect API Gateway REST endpoints coupled with SQS queues for asynchronous AI payload handling. | 19/11/2024 | 19/11/2024      | Backend Codebase, AWS Rekognition, [Workshop 5.7](5-Workshop/5.6-AI-Service/)  |
| Wed | - **Integration Regression:** Diagnosed system-wide failures post-AI integration, necessitating a full stack teardown. <br> - **Contingency Engineering:** Deployed a redundant, optimized backup Multi-Stack configured by the Team Leader to ensure development continuity.                                                                                      | 20/11/2024 | 20/11/2024      | Leader's Backup Stack                                                          |
| Thu | - **Diagnostic Resolution:** Conducted root-cause analysis on re-emerging CORS violations. <br> - **Configuration Hardening:** Enforced rigid header synchronization across API Gateway and Lambda. <br> - **Security Implementation:** Defined IAM Roles, integrated Secrets Manager for API credentials, and deployed WAF rules.                                 | 21/11/2024 | 21/11/2024      | API Gateway/Lambda Configuration, [Workshop 5.9](5-Workshop/5.9-Security-IAM/) |
| Fri | - **System Stabilization:** Synchronized the team on the new Frontend architecture and finalized the primary Stack configuration. <br> - **Architectural Freeze:** Adopted the decoupled stack strategy to facilitate future scalability and independent maintenance.                                                                                              | 22/11/2024 | 22/11/2024      | New Structure Report                                                           |

---

### Week 11 Outcomes

**Technical Transformation & Integration:**

-   **Knowledge Deepening:** Enhanced serverless acumen through **AWS Cloud Mastery Series**, specifically in Rekognition integration and AuthZ error handling.
-   **Frontend Homogenization:** Successfully refactored the client-side architecture, establishing a consistent pattern for future development.
-   **Multi-Stack Operationalization:** Transitioned from a monolithic SAM template to a **Multi-Stack architecture**, significantly reducing deployment times and blast radius.
-   **CORS Remediation:** Permanently rectified persistent CORS anomalies by aligning Gateway and Application layer configurations.
-   **Deployment Mastery:** Acquired advanced troubleshooting skills for SAM Template validation and CloudFormation rollback errors.
-   **Architectural Redundancy:** Established a "Backup Stack" protocol to maintain project velocity during major architectural refactors.
-   **Phase Transition:** Successfully moved the project into the **AI Functional Testing** phase with a robust troubleshooting framework in place.

**Workshop Progress - AI Architecture, Security & Observability:**

-   **API Orchestration:** Configured API Gateway REST API with dedicated endpoints (`/writing/evaluate`, `/speaking/evaluate`, `/flashcard/generate`).
-   **Asynchronous Decoupling:** Provisioned **SQS queues** (writing, speaking, flashcard) to buffer requests and decouple API from compute.
-   **Compute & AI:** Deployed Lambda functions (`writing_evaluator`, `speaking_evaluator`, `rag_flashcard`) integrating **Amazon Bedrock** and **Google Gemini API**.
-   **NoSQL Persistence:** Configured DynamoDB tables for storing evaluation results and generated flashcard sets.
-   **Secrets Management:** Integrated **AWS Secrets Manager** to securely rotate and inject API keys at runtime.
-   **Security Posture:**
    -   Enforced **Least-Privilege** access via granular IAM Roles.
    -   Deployed **AWS WAF** Web ACLs for application-layer defense.
-   **Observability:** Enabled **CloudWatch Logs & Alarms** for error tracking and **CloudWatch Insights** for deep log analytics.

**Core Insights:**

-   **Decoupling is Key:** Splitting a monolith into Multi-Stacks improves deploy speed and manageability.
-   **Async for AI:** AI processes are slow; using SQS allows the API to respond immediately while Lambda processes in the background (Event-Driven Architecture).
-   **Security First:** Never hardcode API keys; Secrets Manager is mandatory for production-grade security.
-   **Observability:** CloudWatch Alarms are essential to detect Lambda timeouts or throttling before users report them.
