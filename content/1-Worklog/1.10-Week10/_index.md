---
title: "Worklog Week 10"
date: 2024-11-11
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Goals

-   **Environment Stabilization:** Solidify the AWS SAM/Serverless deployment pipeline and remediate critical instability factors.
-   **Diagnostic Resolution:** Systematically debug interoperability bottlenecks, specifically CORS misconfigurations and template validation failures.
-   **Full-Stack Integration:** Fuse the Frontend and Backend layers to facilitate End-to-End (E2E) testing via the user interface.
-   **CRUD Validation:** Finalize and validate **Read** and **Delete** logic with robust error handling.
-   **Expert Consultation:** Leverage insights from the **AWS Cloud Mastery Series** to address architectural roadblocks.
-   **Workshop Execution:** Architect the Ingress layer using **Application Load Balancer (ALB)** for intelligent traffic distribution.

---

### Weekly Task Execution

| Day | Activity                                                                                                                                                                                                                                                                                                                                                    | Start Date | Completion Date | Resources                                                                       |
| :-- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :------------------------------------------------------------------------------ |
| Mon | - **CORS Rectification:** Harmonize **API Gateway** preflight (OPTIONS) configurations with Lambda response headers to authorize Frontend consumption. <br> - **Template Sanitation:** Refactor `template.yaml` to resolve circular dependencies and prevent validation failures during `sam deploy`.                                                       | 11/11/2024 | 11/11/2024      | API Gateway/CORS Documentation                                                  |
| Tue | - **Query Logic Optimization:** Fortify the **Read** function to ensure accurate DynamoDB querying and standardized JSON payload formatting. <br> - **Resiliency:** Implement exception handling for null datasets and invalid query parameters. <br> - **Observability:** Inject structured logging for runtime debugging.                                 | 12/11/2024 | 12/11/2024      | DynamoDB Query Documentation                                                    |
| Wed | - **Client Integration:** Merge the Frontend codebase with the deployed API to validate data rendering. <br> - **UI Verification:** Successfully rendered flashcard collections on React/Vue components. <br> - **Workshop Activity:** Provision Application Load Balancer (ALB) in public subnets and map Target Groups.                                   | 13/11/2024 | 13/11/2024      | Frontend Framework Documentation, [Workshop 5.5](5-Workshop/5.5-Load-Balancer/) |
| Thu | - **Delete Logic Deployment:** Roll out the implementation for resource removal. <br> - **AuthZ Bottleneck:** Identified a critical failure in extracting **Cognito User Sub ID** from JWT tokens within Lambda, blocking privileged operations. <br> - **Investigation:** Initiated deep-dive troubleshooting of the authentication flow.                  | 14/11/2024 | 14/11/2024      | AWS Cognito Documentation                                                       |
| Fri | - **Strategic Mentorship:** Attended **AWS Cloud Mastery Series** to gain expert perspective on Serverless patterns and AuthZ best practices. <br> - **Remediation Strategy:** Applied mentor guidance to refactor the Cognito token parsing logic for Update/Delete operations. <br> - **Knowledge Base:** Documented resolution steps for team reference. | 15/11/2024 | 15/11/2024      | Mentor, AWS Cloud Mastery Series                                                |

---

### Week 10 Outcomes

**Technical Stabilization & Integration:**

-   **Configuration Resolution:** Successfully mitigated persistent CORS errors and stabilized the SAM deployment loop, ensuring a reliable CI/CD flow.
-   **Expert Alignment:** Gained critical architectural direction from the **AWS Cloud Mastery Series**, directly addressing project blockers.
-   **E2E Connectivity:** Achieved the first successful **Frontend-Backend Integration**, enabling functional UI testing.
-   **Operational CRUD:** Deployed functional **Read** and **Delete** operations, now accessible via the web interface.
-   **Bottleneck Identification:** Pinpointed specific authorization failures:
    -   **Context Extraction:** Lambda's inability to correctly parse **Cognito Sub ID** from the authorization header.
    -   **Dependency Blocking:** Update/Delete functions stalled due to strict identity verification requirements.
-   **Testing Phase:** Transitioned the project into the User Acceptance Testing (UAT) phase for basic operations.
-   **Workflow Standards:** Established debugging protocols and error handling standards for the development team.

**Workshop Progress - Load Balancer Configuration:**

-   **Ingress Architecture:** Provisioned an Application Load Balancer (ALB) spanning two Availability Zones (Public Subnets).
-   **Traffic Routing:** Configured Target Groups for ECS services (Frontend: 3000, Backend: 8080).
-   **Health Monitoring:** Implemented automated health checks to evict unhealthy targets.
-   **Security Offloading:** Configured **SSL/TLS termination** using ACM certificates to offload encryption overhead.
-   **DNS Integration:** Mapped ALB endpoints to Route 53 for domain resolution.
-   **Path-Based Routing:** Defined listener rules to segregate traffic (Frontend: `/`, Backend: `/api/*`).
-   **Network Security:** Applied security group rules permitting strict ALB-to-ECS traffic flow.

**Core Insights:**

-   **CORS Complexity:** CORS compliance requires a synchronized configuration across both the Gateway (Preflight) and Application (Headers) layers.
-   **Identity Context:** Raw JWT tokens must be meticulously decoded to extract the **User Sub ID** for granular authorization.
-   **Contract Adherence:** Successful integration hinges on strict adherence to API contracts and data serialization formats between Client and Server.
-   **Observability:** Comprehensive logging is the only defense against obscure production runtime errors.
-   **ALB Efficiency:** Application Load Balancers provide critical intelligence (Path routing) and performance benefits (SSL Offloading) for containerized workloads.
