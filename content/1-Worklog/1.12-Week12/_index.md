---
title: "Worklog Week 12"
date: 2024-11-25
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Week 12 Goals

-   **Functional Completion:** Achieve 100% completion of CRUD operations and AI-driven image processing pipelines (inclusive of Update logic).
-   **Architectural Resilience:** Re-architect the image processing workflow using **Amazon SQS** to introduce asynchronous decoupling and load buffering.
-   **Feature Parity:** Finalize auxiliary capabilities including Security hardening, Geospatial (Map Pinning) integration, and SNS notifications.
-   **Presentation Readiness:** Polish the Frontend UX/UI, strategize domain acquisition, and validate the final build via the **AWS Cloud Mastery Series**.

---

### Weekly Task Execution

| Day | Activity                                                                                                                                                                                                                                                           | Start Date | Completion Date | Resources                                  |
| :-- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :----------------------------------------- |
| Mon | - **Codebase Stabilization:** Eliminate residual bugs in the Update function and AI integration (specifically Sub ID extraction and Rekognition logic) to ensure functional integrity.                                                                             | 25/11/2024 | 25/11/2024      | Mentor Guidance, Backend Codebase          |
| Tue | - **Asynchronous Decoupling:** Inject **AWS SQS** into the AI pipeline to buffer requests, enabling a scalable Event-Driven Architecture. <br> - **Flow Definition:** Re-map the data ingestion path: Upload -> S3 Event -> SQS -> Lambda (AI Worker) -> DynamoDB. | 26/11/2024 | 26/11/2024      | AWS SQS Documentation, Lambda Architecture |
| Wed | - **UX/UI Finalization:** Complete the development of core Frontend views (Dashboard, Detail View, User Profile). <br> - **Geospatial Integration:** Implement **Map Pinning** logic by persisting and rendering geospatial coordinates from DynamoDB.             | 27/11/2024 | 27/11/2024      | Frontend Codebase, DynamoDB Geo            |
| Thu | - **Security Hardening:** Refine IAM Policies and Cognito claims to ensure precise `Sub` ID retrieval for resource ownership authorization. <br> - **Notification System:** Integrate **AWS SNS** to trigger push notifications upon successful post processing.   | 28/11/2024 | 28/11/2024      | AWS SNS, Cognito/IAM Documentation         |
| Fri | - **Expert Validation:** Attend the final **AWS Cloud Mastery Series** for a pre-demo review and architectural sign-off. <br> - **DNS Strategy:** Finalize domain name selection and prepare Route 53 hosted zones for production cutover.                         | 29/11/2024 | 29/11/2024      | Mentor, AWS Cloud Mastery Series, Route 53 |

---

### Week 12 Outcomes

**System Maturity & Demo Readiness:**

-   **Functional Milestone:** Achieved **100% completion** of core CRUD and AI Image Processing features, delivering a stable and responsive backend.
-   **Architectural Upgrade:** Successfully implemented an **Event-Driven Architecture** using SQS, decoupling the ingestion layer from the processing layer for enhanced reliability.
-   **Feature Completeness:** Shipped critical enhancements including AuthZ hardening, Geospatial visualization (Map Pinning), and Event notifications (SNS).
-   **Frontend Polish:** Delivered a presentation-ready User Interface with fully realized user flows.
-   **Strategic Alignment:** Validated the final solution architecture through the **AWS Cloud Mastery Series**, ensuring adherence to best practices.
-   **Go-Live Prep:** Completed domain research and DNS planning for the public launch.
-   **Status:** The project has officially reached **Demo Readiness**, prepared for final presentation and evaluation.
