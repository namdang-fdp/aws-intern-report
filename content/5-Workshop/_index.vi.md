---
title: "Workshop"
date: 2025-09-09
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Triển khai nền tảng IELTS BandUp tích hợp AI trên hạ tầng AWS

#### Giới thiệu

Chào mừng đến với **Workshop Triển khai IELTS BandUp**.

**IELTS BandUp** là một nền tảng công nghệ giáo dục (EdTech) toàn diện, được thiết kế để đồng hành cùng người học trong suốt hành trình chinh phục kỳ thi IELTS. Ứng dụng cung cấp một hệ sinh thái tính năng đa dạng bao gồm: Thi thử trọn vẹn (Full Mock Tests), Luyện nghe chép chính tả (Dictation), Blog chia sẻ kiến thức và Flashcards tương tác.

Để nâng cao trải nghiệm học tập, hệ thống tích hợp **Generative AI** đóng vai trò như một trợ lý học tập thông minh. Tận dụng sức mạnh của các mô hình từ AWS Bedrock và Google Gemini, nền tảng cung cấp phản hồi chi tiết và hỗ trợ cá nhân hóa, đảm bảo phương pháp tiếp cận toàn diện cho việc ôn luyện thay vì chỉ dừng lại ở việc chấm điểm đơn thuần.

Trong workshop này, chúng ta sẽ thực hiện quy trình triển khai từ đầu đến cuối (end-to-end) kiến trúc hiện đại này lên đám mây AWS. Nội dung bao gồm thiết lập hạ tầng mạng, điều phối ứng dụng container, quản lý cơ sở dữ liệu, tích hợp module AI serverless và xây dựng quy trình chuyển giao tự động.

#### Mục tiêu Workshop

Sau khi hoàn thành workshop này, chúng ta sẽ đạt được các mục tiêu sau:

-   **Kiến trúc mạng (Network Architecture):** Thiết lập một VPC an toàn với các phân vùng mạng (Subnets) Public/Private, NAT Gateway và Application Load Balancer để đảm bảo luồng truy cập bảo mật.
-   **Điều phối Container:** Triển khai các dịch vụ Frontend (Next.js) và Backend (Spring Boot) sử dụng **AWS ECS Fargate**.
-   **Quản lý dữ liệu:** Cấu hình hệ thống cơ sở dữ liệu có tính sẵn sàng cao (High Availability) với **Amazon RDS** (Primary/Standby) và **Amazon ElastiCache**.
-   **Tích hợp AI:** Triển khai kiến trúc Serverless sử dụng **AWS Lambda, API Gateway và Amazon Bedrock** để xử lý các tác vụ đánh giá AI một cách bất đồng bộ.
-   **DevOps:** Tự động hóa quy trình xây dựng (Build) và triển khai (Deploy) với **AWS CodePipeline và CodeBuild**.

#### Nội dung

1. [Tổng quan dự án & Kiến trúc hệ thống](5.1-Workshop-overview/)
2. [Chuẩn bị & Thiết lập hạ tầng](5.2-Prerequiste/)
3. [Thiết lập Hạ tầng Mạng & Bảo mật](5.3-Network/)
4. [Triển khai Frontend (ECS Fargate)](5.4-Setup-FE/)
5. [Triển khai Backend (ECS Fargate)](5.5-Setup-BE/)
6. [Tích hợp dịch vụ AI (Serverless)](5.6-Setup-AI/)
7. [Triển khai CI/CD Pipeline](5.7-CICD/)
