---
title: "Worklog Tuần 4"
date: 2025-09-09
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4

-   Đồng bộ tốc độ học tập kỹ thuật với đà phát triển chung của toàn nhóm về hệ sinh thái AWS.
-   Làm chủ kiến trúc AWS Transit Gateway để quản lý mạng tập trung.
-   Nâng cao năng lực cốt lõi về Amazon EC2 và các dịch vụ tính toán (compute) mở rộng.
-   Thành thạo quy trình quản lý phiên bản với Git để tăng cường hiệu quả làm việc nhóm.
-   **Khởi tạo Workshop:** Thiết lập hạ tầng VPC & Mạng nền tảng cho dự án Bandup IELTS.

### Nhiệm vụ thực hiện trong tuần

| Ngày | Hoạt động                                                                                                                                                                                                                                                                                                                 | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                                                                   |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ------------------------------------------------------------------------------------ |
| 2    | - **Kiến trúc mạng:** Nghiên cứu sâu về khái niệm, quy trình triển khai và các điều kiện tiên quyết của AWS Transit Gateway.<br>- **Phân tích so sánh:** Đánh giá sự khác biệt về kiến trúc giữa VPC Peering và Transit Gateway.<br>- **Hoàn thành:** Học phần _Centralized Network Management with AWS Transit Gateway_. | 29/09/2025   | 30/09/2025      | [AWS Transit Gateway](https://aws.amazon.com/transit-gateway/)                       |
| 3    | - **Nghiên cứu Compute nâng cao:** Tìm hiểu sâu về Amazon EC2 thông qua bài giảng Module 3.<br>- **Triển khai tính đàn hồi:** Làm chủ việc cấp phát tài nguyên tự động sử dụng EC2 Auto Scaling.<br>- **Hoàn thành:** Học phần _Scaling Applications with EC2 Auto Scaling_.                                              | 01/10/2025   | 02/10/2025      | [FCJ Playlist](https://youtube.com/playlist?list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i) |
| 4    | - **Quản lý phiên bản:** Chuẩn hóa quy trình hợp tác sử dụng các thao tác Git (commit, push, pull).<br>- **Compute rút gọn:** Đánh giá Amazon Lightsail cho các nhu cầu VPS đơn giản hóa.<br>- **Hoàn thành:** Học phần _Simplified Computing with Amazon Lightsail_.                                                     | 03/10/2025   | 04/10/2025      | [Git Tutorial](https://www.youtube.com/watch?v=8O14qT3jdq0)                          |
| 5    | - **Quản trị dự án:** Điều phối phân chia nhiệm vụ và chốt chiến lược cho bản đề xuất dự án.<br>- **Chiến lược di dời:** Phân tích tính linh động của workload sử dụng AWS VM Import/Export.<br>- **Thực thi Workshop:** Kiến trúc và khởi tạo môi trường VPC ban đầu (CIDR `10.0.0.0/16`) bao gồm cấu hình DNS.          | 05/10/2025   | 06/10/2025      | Team Meeting, [Workshop 5.3](5-Workshop/5.3-VPC-Network/)                            |

### Các khóa học AWS Skill Builder đã hoàn thành

| Khóa học                                                | Danh mục    | Trạng thái |
| ------------------------------------------------------- | ----------- | ---------- |
| Centralized Network Management with AWS Transit Gateway | Networking  | ✅         |
| Scaling Applications with EC2 Auto Scaling              | Compute     | ✅         |
| Simplified Computing with Amazon Lightsail              | Compute     | ✅         |
| Container Deployment with Amazon Lightsail Containers   | Containers  | ✅         |
| VM Migration with AWS VM Import/Export                  | Migration   | ✅         |
| Database Migration with AWS DMS and SCT                 | Migration   | ✅         |
| Disaster Recovery with AWS Elastic Disaster Recovery    | Reliability | ✅         |
| Monitoring with Amazon CloudWatch                       | Operations  | ✅         |

### Kết quả đạt được trong tuần 4

**Năng lực kỹ thuật:**

_Kiến trúc AWS Transit Gateway:_

-   Thiết kế mô hình mạng trung tâm (hub) sử dụng Transit Gateway.
-   Xác định các ưu thế chiến lược so với VPC Peering:
    -   Khả năng hỗ trợ mô hình tô-pô phức tạp dạng **hub-and-spoke**.
    -   Cho phép **định tuyến bắc cầu (transitive routing)** giữa các mạng kết nối.
    -   Đơn giản hóa vận hành khi mở rộng quy mô kết nối mạng.
    -   Tích hợp liền mạch với VPN và Direct Connect.
-   Có chuyên môn trong việc quản lý bảng định tuyến (route table) của Transit Gateway.

_Amazon EC2 & Tính đàn hồi của Compute:_

-   Đạt trình độ chuyên sâu về các tính năng cốt lõi của EC2:
    -   **Tính đàn hồi:** Tận dụng cơ chế auto-scaling để thích ứng với tải động.
    -   **Tối ưu hóa Workload:** Lựa chọn các dòng instance phù hợp cho từng tác vụ cụ thể.
    -   **Hiệu quả chi phí:** Sử dụng linh hoạt các mô hình giá On-Demand, Reserved và Spot.
-   Làm chủ **EC2 Auto Scaling** để quản lý đội tàu (fleet) máy chủ tự động.
-   Hiểu rõ đặc tính của **Instance Store** như một giải pháp lưu trữ tạm thời hiệu năng cao.
-   Đánh giá **Amazon Lightsail** cho việc triển khai nhanh các ứng dụng và container quy mô nhỏ.

_Di dời (Migration) & Khả năng phục hồi:_

-   Phân tích **AWS Application Migration Service (MGN)** cho các hoạt động lift-and-shift.
-   Tìm hiểu phương pháp **VM Import/Export** cho tính linh động của hybrid cloud.
-   Xem xét chiến lược chuyển đổi cơ sở dữ liệu sử dụng **DMS** và **SCT**.
-   Xây dựng kế hoạch đảm bảo hoạt động kinh doanh liên tục (BCP) sử dụng **AWS Elastic Disaster Recovery**.

_DevOps & Khả năng quan sát:_

-   Củng cố quy trình quản lý phiên bản **Git** cho sự hợp tác nhóm phân tán.
-   Nắm bắt các nguyên lý cơ bản của **Amazon CloudWatch** để giám sát và quan sát tài nguyên.

**Tiến độ hợp tác nhóm:**

-   Dẫn dắt buổi thảo luận và chốt lộ trình cho bản đề xuất dự án.
-   Đưa nhóm bước vào giai đoạn thực thi (implementation) với tâm thế sẵn sàng cao.
-   Xác định và phân công vai trò, trách nhiệm cụ thể cho từng thành viên.

**Tiến độ Workshop - Hạ tầng VPC & Mạng:**

-   **Hạ tầng cốt lõi:** Khởi tạo VPC chính với CIDR `10.0.0.0/16` tại region `ap-southeast-1`.
-   **Phân đoạn mạng (Network Segmentation):** Triển khai kiến trúc subnet đa tầng:
    -   Public Tier: `10.0.1.0/24`, `10.0.2.0/24`.
    -   Application Tier (Private): `10.0.11.0/24`, `10.0.12.0/24`.
    -   Database Tier (Private): `10.0.21.0/24`, `10.0.22.0/24`.
-   **Kết nối:** Thiết lập Internet Gateway để đảm bảo truy cập Ingress/Egress công khai.
-   **Logic định tuyến:** Cấu hình route table để kiểm soát chặt chẽ luồng giao thông giữa các tầng.
-   **Lớp bảo mật:** Khởi tạo các định nghĩa Security Group để thực thi vi phân đoạn (micro-segmentation).

**Đúc kết cốt lõi:**

-   **Transit Gateway** đóng vai trò xương sống quan trọng cho các kiến trúc định tuyến đa VPC quy mô lớn.
-   **EC2 Auto Scaling** là yếu tố bắt buộc để đảm bảo tính sẵn sàng cao và tối ưu chi phí dưới tải trọng biến động.
-   **Các dịch vụ Migration** cung cấp đa dạng lộ trình (Rehost, Replatform) để tăng tốc độ chuyển đổi lên mây.
-   **Thiết kế VPC** với sự cô lập nghiêm ngặt Public/Private là nền tảng của hạ tầng đám mây an toàn.
-   **Kiến trúc Multi-AZ** hoạt động như tuyến phòng thủ đầu tiên cho khả năng phục hồi mạng và chịu lỗi.
