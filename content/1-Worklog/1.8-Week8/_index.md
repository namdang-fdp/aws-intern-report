---
title: "Week 8 Worklog"
date: 2024-10-28
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Goals

-   **Academic Milestone:** Successfully navigate the mid-term assessment (October 31st) with high proficiency.
-   **Backend Initialization:** Initiate the development of core **CRUD (Create, Read, Update, Delete)** logic for the **Bandup IELTS** ecosystem.
-   **Serverless Strategy:** Architect the integration of **AWS Serverless primitives** (Lambda, API Gateway, DynamoDB) into the project topology.
-   **Environment Provisioning:** Establish a robust local development environment and project scaffolding.

---

### Weekly Task Execution

| Day       | Activity                                                                                                                                                                                                                                                                                                 | Start Date | Completion Date | Resources                                      |
| :-------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :--------------------------------------------- |
| Monday    | - **Pre-Exam Consolidation:** Execute final knowledge synthesis. Review architectural nuances (IAM Policies vs Roles, Security Layers, VPC Routing logic). <br> - **Simulation:** Optimize time management strategies for the examination context.                                                       | 28/10/2024 | 28/10/2024      | Personal notes, AWS Builders                   |
| Tuesday   | - **Environment Engineering:** Configure the local toolchain including Python environment, AWS CLI authentication, and IDE extensions. <br> - **Readiness:** Ensure mental and technical preparedness for the upcoming assessment.                                                                       | 29/10/2024 | 30/10/2024      | AWS CLI Documentation                          |
| Wednesday | - **Assessment Execution:** Undertake the **Mid-term Exam** on October 31st. <br> - **Retrospective:** Conduct a post-exam analysis to identify performance strengths and areas for theoretical reinforcement.                                                                                           | 31/10/2024 | 31/10/2024      | Exam Venue                                     |
| Thursday  | - **Serverless Prototyping:** Engineer the initial **'Create'** vector for the Flashcard module. <br> - **Compute & Storage:** Deploy experimental **AWS Lambda** functions and design the **DynamoDB** schema for high-performance data access.                                                         | 01/11/2024 | 01/11/2024      | AWS Lambda & DynamoDB documentation            |
| Friday    | - **API Orchestration:** Design the RESTful interface via **API Gateway**. <br> - **Data Flow Architecture:** Map the ingress/egress path: Frontend → API Gateway → Lambda → DynamoDB. <br> - **Logic Implementation:** Code the **'Read'** handler to retrieve flashcard datasets from the NoSQL store. | 02/11/2024 | 02/11/2024      | API Gateway documentation, Serverless patterns |

---

### Week 8 Outcomes

**Academic & Technical Progress:**

-   **Academic Success:** Concluded the mid-term examination phase (October 31st), validating the foundational knowledge acquired.
-   **DevOps Readiness:** Fully provisioned the development environment, integrating Python and AWS CLI for streamlined workflow.
-   **Backend Logic:** Deployed the initial **Create/Read** micro-functionalities for **Bandup IELTS** utilizing a serverless stack.
-   **Architectural Blueprint:** Validated the Serverless triad for the project:
    -   **API Gateway** serving as the secure HTTP entry point.
    -   **Lambda** executing business logic in an event-driven manner.
    -   **DynamoDB** providing low-latency NoSQL persistence.
-   **Competency Deepening:** Solidified expertise in serverless components critical for modern application development.
-   **Project Governance:** Established a clean project directory structure to support future scalability.
-   **Code Delivery:** Shipped the first functional Lambda handler for data ingestion.

**Core Insights:**

-   **Operational Efficiency:** Serverless architecture abstracts infrastructure management, significantly reducing operational overhead.
-   **Event-Driven Scaling:** Lambda functions offer automatic scaling triggered by specific request events.
-   **Performance:** DynamoDB delivers consistent single-digit millisecond latency for high-throughput workloads.
-   **Gateway Pattern:** API Gateway acts as the centralized orchestrator for API management, security, and throttling.
-   **Scaffolding:** Establishing a proper project structure early is crucial for long-term maintainability.
