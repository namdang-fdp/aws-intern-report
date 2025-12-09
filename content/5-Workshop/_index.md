---
title: "Workshop"
date: 2025-09-09
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Building a Scalable AI-Powered IELTS Platform on AWS

#### Introduction

Welcome to the **IELTS BandUp Deployment Workshop**.

**IELTS BandUp** is a comprehensive EdTech platform designed to support learners throughout their entire IELTS preparation journey. The application provides a diverse ecosystem of features including full Mock Tests, Dictation practice, Blogs, and interactive Flashcards.

To further enhance the learning experience, the system integrates **Generative AI** as a comprehensive study assistant. By leveraging AWS Bedrock and Google Gemini models, the platform offers intelligent feedback and personalized support, ensuring a holistic approach to exam preparation rather than just simple scoring.

In this workshop, we will demonstrate the end-to-end journey of deploying this modern, microservices-based architecture to the AWS Cloud. We will cover infrastructure setup, container orchestration, database management, serverless AI integration, and automated delivery pipelines.

#### Workshop Objectives

By following this workshop, we will achieve the following:

-   **Network Architecture:** Configure a secure VPC with Public/Private subnets, NAT Gateways, and Application Load Balancers to ensure secure traffic flow.
-   **Container Orchestration:** Deploy Frontend (Next.js) and Backend (Spring Boot) services using **AWS ECS Fargate**.
-   **Data Management:** Configure high-availability databases using **Amazon RDS** (Primary/Standby) and **Amazon ElastiCache**.
-   **AI Integration:** Implement a Serverless architecture using **AWS Lambda, API Gateway, and Amazon Bedrock** to handle AI evaluation tasks asynchronously.
-   **DevOps:** Automate the build and deployment process with **AWS CodePipeline and CodeBuild**.

#### Content

1. [Project Overview & Architecture](5.1-Workshop-overview/)
2. [Prerequisites & Infrastructure Setup](5.2-Prerequiste/)
3. [Network & Security Infrastructure](5.3-Network/)
4. [Frontend Deployment (ECS Fargate)](5.4-Setup-FE/)
5. [Backend Deployment (ECS Fargate)](5.5-Setup-BE/)
6. [AI Services Integration (Serverless)](5.6-Setup-AI/)
7. [CI/CD Pipeline Implementation](5.7-CICD/)
