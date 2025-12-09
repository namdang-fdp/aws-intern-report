---
title: "Week 9 Worklog"
date: 2024-11-04
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Goals

-   **Framework Migration:** Execute full migration of the development workflow to **AWS SAM (Serverless Application Model)**.
-   **Architectural Modernization:** Refactor CRUD logic to align with SAM-native serverless patterns.
-   **Environment Standardization:** Mitigate local runtime discrepancies to achieve a successful cloud deployment.
-   **Containerization:** Implement **Docker** to standardize build pipelines and dependency resolution.
-   **Workshop Execution:** Orchestrate the deployment of containerized Frontend and Backend microservices via **Amazon ECS**.

---

### Weekly Task Execution

| Day       | Activity                                                                                                                                                                                                                                                                                                                                                                                                      | Start Date | Completion Date | Resources                                                                |
| :-------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--------- | :-------------- | :----------------------------------------------------------------------- |
| Monday    | - **SAM Framework Analysis:** Dissect the anatomy of `template.yaml`, SAM CLI operations, and the interplay between Lambda and API Gateway resources. <br> - **Migration Roadmap:** Formulate a strategy to convert legacy Lambda functions into SAM-compliant resources. <br> - **Local Emulation:** Evaluate local testing capabilities via `sam local invoke`.                                             | 04/11/2024 | 04/11/2024      | AWS SAM Documentation, AWS Study Group                                   |
| Tuesday   | - **Codebase Modernization:** Re-architect Create/Read handlers to leverage SAM event sources. <br> - **Container Strategy:** Configure **Docker** to guarantee Python runtime consistency during `sam build`. <br> - **Layer Management:** Engineer Dockerfiles for Lambda dependency layers. <br> - **Workshop Activity:** Provision ECR repositories for container artifact management.                    | 05/11/2024 | 06/11/2024      | Docker Documentation, SAM CLI, [Workshop 5.4](5-Workshop/5.4-ECS-Setup/) |
| Wednesday | - **Local Simulation:** Conduct unit testing via local invocation. <br> - **Environment Divergence:** Identified critical blockers in local emulation (Dependency conflicts, Python version mismatch, DynamoDB local connectivity). <br> - **Troubleshooting:** Attempted reconfiguration to align local and remote environments.                                                                             | 06/11/2024 | 07/11/2024      | SAM CLI Error Reports, Stack Overflow                                    |
| Thursday  | - **Strategic Pivot:** Adopted a **"Cloud-First Verification"** strategy (deploy-then-test) to bypass local emulation bottlenecks. <br> - **Template Optimization:** Refined `template.yaml` definitions, IAM policies, and environment variables. <br> - **Validation:** Audited template syntax and resource dependencies.                                                                                  | 07/11/2024 | 08/11/2024      | CloudFormation Template Validator                                        |
| Friday    | - **Production Deployment:** Successfully executed `sam deploy --guided` to provision the stack on AWS. <br> - **Endpoint Validation:** Verified API integrity and CRUD operations via Postman/cURL. <br> - **Documentation:** Codified the deployment pipeline for team adoption. <br> - **Workshop Activity:** Orchestrated ECS Fargate deployment (Task Definitions, Service creation, and Image pushing). | 08/11/2024 | 08/11/2024      | AWS CloudFormation Logs, [Workshop 5.4](5-Workshop/5.4-ECS-Setup/)       |

---

### Week 9 Outcomes

**Technical Transformation:**

-   **Framework Migration Success:** Completed the strategic transition to **AWS SAM**, establishing Infrastructure as Code (IaC) for serverless resources.
-   **Architectural Refactoring:** Successfully modernized CRUD handlers into a modular SAM structure.
-   **Dependency Resolution:** Leveraged **Docker** to enforce build consistency, eliminating "works on my machine" issues.
-   **Deployment Breakthrough:** Overcame local debugging limitations by shifting to a cloud-based verification workflow, resulting in the first successful live API deployment.
-   **Milestone:** The **Bandup IELTS** API is now operational in a real cloud environment.
-   **Governance:** Established a repeatable deployment workflow and a comprehensive `template.yaml` acting as the single source of truth.

**Workshop Progress - ECS & Container Orchestration:**

-   **Artifact Management:** Established ECR repositories for Frontend (Next.js) and Backend (Spring Boot).
-   **Build Pipeline:** Executed Docker build and push operations with semantic tagging strategies.
-   **Task Specification:** Defined granular ECS Task Definitions (Frontend: 0.5 vCPU/1GB, Backend: 1 vCPU/2GB).
-   **Cluster Orchestration:** Provisioned ECS Cluster leveraging Fargate capacity providers.
-   **High Availability:** Deployed ECS Services in an Active-Passive Multi-AZ configuration (2 active replicas, 1 standby).
-   **Service Mesh:** Configured **Service Connect** for seamless internal service discovery.
-   **Resiliency:** Implemented automated health checks for task auto-recovery.

**Core Insights:**

-   **IaC Power:** SAM simplifies serverless complexity by treating infrastructure as code.
-   **Container Consistency:** Docker is non-negotiable for consistent build environments across heterogeneous development machines.
-   **Strategic Adaptation:** Recognizing when to abandon local emulation in favor of cloud-based testing is a crucial DevOps skill.
-   **IAM Precision:** SAM templates enforce strict permission boundaries, critical for secure Lambda execution.
-   **Fargate Abstraction:** ECS Fargate removes the operational overhead of managing EC2 instances for containers.
-   **Service Connect:** Simplifies internal microservice communication, reducing the need for complex internal load balancers.
