---
title: "Week 3 Worklog"
date: 2025-09-21
weight: 3
chapter: false
pre: "<b>1.3. </b>"
---

### Week 3 Goals

-   Rectify AWS account discrepancies and provision a fresh account if required.
-   Achieve proficiency in Hybrid DNS architecture using Route 53 Resolver.
-   Establish and comprehend private inter-network connectivity via VPC Peering.
-   Strategize the project roadmap and reach a consensus on the development language.

### Weekly Task Execution

| Day | Activity                                                                                                                                                                                                                                                                                                                                               | Start Date | Completion Date | Reference Material                                                                   |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ------------------------------------------------------------------------------------ |
| 2   | - **Identity Governance:** Implement access controls and permissions utilizing AWS Identity and Access Management (IAM).                                                                                                                                                                                                                               | 21/09/2025 | 23/09/2025      | [AWS IAM Access Control](https://000002.awsstudygroup.com/)                          |
| 3   | - **Lab Execution:** Perform Lab 10 focused on Hybrid DNS and Route 53 setup.<br>- **Deployment:** Spin up EC2 instances to validate DNS resolution logic.<br>- **Completion:** Finished module _Hybrid DNS Management with Amazon Route 53_.                                                                                                          | 24/09/2025 | 25/09/2025      | [FCJ Playlist](https://youtube.com/playlist?list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i) |
| 4   | - **Network Integration:** Configure VPC Peering to facilitate private traffic flow between distinct VPCs.<br>- **Resource Provisioning:** Deploy necessary assets to support the peering topology.<br>- **Teardown:** Decommission resources post-lab to optimize costs.<br>- **Completion:** Finished module _Network Integration with VPC Peering_. | 25/09/2025 | 26/09/2025      | [AWS VPC Peering](https://docs.aws.amazon.com/vpc/latest/peering/)                   |
| 5   | - **Strategic Planning:** Engage in a team sync to finalize the tech stack and project direction.<br>- **Scheduling:** Define milestones for team members to ramp up on the selected technology.                                                                                                                                                       | 28/09/2025 | 28/09/2025      | Team Meeting                                                                         |

### AWS Skill Builder Curriculum Completed

| Course                                         | Category    | Status |
| ---------------------------------------------- | ----------- | ------ |
| Hybrid DNS Management with Amazon Route 53     | Networking  | ✅     |
| Network Integration with VPC Peering           | Networking  | ✅     |
| Networking on AWS Workshop                     | Networking  | ✅     |
| Infrastructure as Code with AWS CloudFormation | DevOps      | ✅     |
| Cloud Development with AWS Cloud9              | Development | ✅     |
| Static Website Hosting with Amazon S3          | Storage     | ✅     |

### Week 3 Outcomes

**Technical Proficiency Gained:**

_Route 53 & Hybrid DNS Architecture:_

-   Orchestrated a robust Hybrid DNS ecosystem leveraging Route 53 Resolver.
    [Image of AWS Hybrid DNS architecture with Route 53 Resolver]
-   Provisioned **Outbound Endpoints** to forward DNS queries from AWS to on-premises environments.
-   Defined granular **Resolver Rules** to manage conditional forwarding logic.
-   Established **Inbound Endpoints** to allow on-premises networks to resolve AWS-hosted domains.
-   Verified connectivity via RD Gateway Server during practical implementation.

_VPC Peering & Network Interconnectivity:_

-   Internalized the mechanics of VPC Peering for securing private communications without public internet exposure.
    [Image of AWS VPC Peering architecture]
-   Activated and tested **DNS Resolution across Zones and Regions** within peered VPCs:
    -   Enabled EC2 instances to resolve peer hostnames to private IP addresses.
    -   Recognized that omitting this configuration forces resolution to public IPs, routing traffic unnecessarily through the internet.
-   Practiced strict resource termination protocols to prevent billing leakage.

_Infrastructure as Code (IaC) & Dev Tools:_

-   Acquired the ability to deploy AWS infrastructure using **CloudFormation** templates.
-   Grasped the paradigm of declarative infrastructure management.
-   Investigated **AWS Cloud9** as a browser-native Integrated Development Environment (IDE).

**Collaborative Progress:**

-   Contributed to high-level project planning sessions to lock in the development trajectory.
-   Reached a unanimous decision on the programming language for the upcoming project.
-   Set clear study timelines for the team to master the chosen technology stack.
-   Maintained active engagement and support within the FCJ team.

**Core Insights:**

-   **Hybrid DNS** acts as a critical bridge for seamless name resolution between legacy on-prem systems and modern cloud environments.
-   **VPC Peering** offers a cost-efficient method for network linking, though it requires awareness of limitations such as the lack of transitive peering.
-   **CloudFormation** ensures infrastructure consistency and repeatability through code.
-   **AWS Cloud9** significantly reduces the friction of setting up local development environments.
