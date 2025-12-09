---
title: "Worklog tuần 5"
date: 2025-10-07
weight: 5
chapter: false
pre: "<b>1.5. </b>"
---

### Mục tiêu tuần 5

-   Kiểm toán và khắc phục các bất thường về chi phí để ổn định ngân sách tài khoản AWS.
-   Kiến trúc và phân đoạn tô-pô hạ tầng cho dự án cốt lõi.
-   Khởi tạo khung sườn mã nguồn (scaffolding) và phân định vai trò, trách nhiệm của nhóm.
-   Tận dụng hệ sinh thái AWS Skill Builder để nâng cao năng lực tối ưu hóa tài nguyên.
-   **Hoàn thiện Workshop:** Củng cố logic Mạng VPC và bắt đầu triển khai **Lớp lưu trữ dữ liệu** (Database & Storage).

### Nhiệm vụ thực hiện trong tuần

| Ngày | Hoạt động                                                                                                                                                                                                                                                                                                                                                          | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                                                                                             |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------ | --------------- | -------------------------------------------------------------------------------------------------------------- |
| 2    | - **Điều tra tài chính:** Phân tích chi tiết hóa đơn để xác định nguyên nhân gốc rễ của việc tăng chi phí.<br>- **Quản trị:** Thiết lập hạn ngạch và giám sát.<br>- **Hoàn thành:** Các học phần _Cost and Usage Management_ và _Managing Quotas with Service Quotas_.                                                                                             | 07/10/2025   | 08/10/2025      | [AWS Cost Explorer](https://aws.amazon.com/aws-cost-management/aws-cost-explorer/)                             |
| 3    | - **Thiết kế hạ tầng:** Phác thảo sơ đồ kiến trúc cấp cao và chiến lược phân vùng.<br>- **Chuẩn hóa:** Đề xuất các bản thiết kế mẫu (blueprints) cho nhóm áp dụng.<br>- **Hoàn thành:** Học phần _Building Highly Available Web Applications_.<br>- **Thực thi Workshop:** Triển khai NAT Gateway cho kết nối ra ngoài an toàn và chốt các tham số Security Group. | 09/10/2025   | 10/10/2025      | [FCJ Community](https://www.facebook.com/groups/awsstudygroupfcj), [Workshop 5.3](5-Workshop/5.3-VPC-Network/) |
| 4    | - **Khởi tạo dự án:** Xây dựng khung mã nguồn ban đầu và các tệp cấu hình.<br>- **Cấu hình IDE:** Tích hợp bộ công cụ AWS vào môi trường phát triển cục bộ.<br>- **Hoàn thành:** Học phần _Development Environment with AWS Toolkit for VS Code_.<br>- **Thực thi Workshop:** Lên chiến lược triển khai RDS PostgreSQL và ElastiCache Redis.                       | 11/10/2025   | 13/10/2025      | VS Code + AWS Toolkit, [Workshop 5.6](5-Workshop/5.6-Database-Storage/)                                        |
| 5    | - **Học tập liên tục:** Tham gia AWS Skill Builder và xây dựng lộ trình học tập.<br>- **Chiến lược tối ưu hóa:** Làm chủ các phương pháp lựa chọn kích cỡ (rightsizing) cho tài nguyên tính toán.<br>- **Hoàn thành:** Học phần _Right-Sizing with EC2 Resource Optimization_.                                                                                     | 11/10/2025   | 12/10/2025      | [AWS Skill Builder](https://skillbuilder.aws/)                                                                 |

### Các khóa học AWS Skill Builder đã hoàn thành

| Khóa học                                             | Danh mục          | Trạng thái |
| ---------------------------------------------------- | ----------------- | ---------- |
| Cost and Usage Management                            | Cost Optimization | ✅         |
| Managing Quotas with Service Quotas                  | Operations        | ✅         |
| Billing Console Delegation                           | Cost Management   | ✅         |
| Right-Sizing with EC2 Resource Optimization          | Cost Optimization | ✅         |
| Development Environment with AWS Toolkit for VS Code | Development       | ✅         |
| Building Highly Available Web Applications           | Architecture      | ✅         |
| Database Essentials with Amazon RDS                  | Database          | ✅         |
| NoSQL Database Essentials with Amazon DynamoDB       | Database          | ✅         |
| In-Memory Caching with Amazon ElastiCache            | Database          | ✅         |
| Command Line Operations with AWS CLI                 | Operations        | ✅         |

### Kết quả đạt được trong tuần 5

**Năng lực kỹ thuật:**

_Tối ưu hóa Chi phí & Quản trị:_

-   **Chẩn đoán các điểm rò rỉ ngân sách:**
    -   Các EBS volume mồ côi và Elastic IP chưa được gỡ bỏ sau khi terminate instance.
    -   Phân quyền IAM lỏng lẻo dẫn đến việc khởi tạo tài nguyên không được kiểm soát.
    -   Tài nguyên "Zombie" vẫn chạy ở các region không hoạt động.
-   **Nắm vững các khung quản trị tài chính:**
    -   **AWS Budgets:** Thiết lập các ngưỡng cảnh báo chi phí chủ động.
    -   **Cost Explorer:** Làm chủ việc phân tích chi tiết xu hướng chi tiêu.
    -   **Service Quotas:** Cấu hình rào chắn để ngăn chặn việc cấp phát quá mức do sơ suất.
    -   **Billing Delegation:** Phân quyền hiển thị chi phí cho các bên liên quan.

_Kỹ thuật Kiến trúc:_

-   **Quy hoạch Hạ tầng:** Chốt tô-pô logic cho hạ tầng dự án.
-   **Kiến trúc tham chiếu:** Phát triển các template chuẩn hóa để đảm bảo tính nhất quán.
-   **Thực thi Tính sẵn sàng cao (HA):**
    -   Kiến trúc chiến lược dự phòng Multi-AZ.
    -   Thiết kế cơ chế Cân bằng tải (Load Balancing) mạnh mẽ.
    -   Định nghĩa các mô hình sao chép Database để chịu lỗi.

_Trải nghiệm Nhà phát triển (DX):_

-   **Tích hợp IDE:** Tích hợp liền mạch AWS Toolkit cho VS Code để tăng tốc quy trình làm việc.
-   **Làm chủ CLI:** Đạt sự thành thạo trong việc thao tác tài nguyên qua dòng lệnh với AWS CLI.
-   **Khởi tạo Dự án:** Xây dựng khung sườn (boilerplate) có khả năng mở rộng với cấu hình ban đầu vững chắc.

_Chiến lược Lưu trữ Dữ liệu:_

-   **Relational:** Xác thực **Amazon RDS** cho các yêu cầu dữ liệu có cấu trúc và giao dịch.
-   **NoSQL:** Đánh giá **DynamoDB** cho các kịch bản thông lượng cao, độ trễ thấp.
-   **Caching:** Lựa chọn **ElastiCache** (Redis) để giảm tải đọc cho database.

**Tiến độ Dự án:**

-   **Tiếp thu Kỹ năng:** Đã tham gia đầy đủ vào hệ sinh thái AWS Skill Builder để liên tục nâng cao trình độ.
-   **Đóng băng Thiết kế:** Kiến trúc hạ tầng đã được rà soát, thống nhất và tài liệu hóa.
-   **Sẵn sàng Code:** Môi trường phát triển đã được cấp phát đầy đủ và tối ưu cho việc cộng tác.

**Tiến độ Workshop - Mạng & Lớp Dữ liệu:**

-   **Kết nối ra ngoài an toàn (Secure Egress):** Thực thi triển khai NAT Gateway trong các public subnet để hỗ trợ truy cập internet an toàn cho các workload private.
-   **Mạng Zero-Trust:** Cấu hình Security Group chi tiết cho các tầng ALB, ECS, RDS và ElastiCache, tuân thủ nguyên tắc đặc quyền tối thiểu.
-   **Logic định tuyến:** Định nghĩa bảng định tuyến chính xác (IGW cho Public, NAT GW cho Private).
-   **Kiến trúc Database:** Thiết kế lớp RDS PostgreSQL với Multi-AZ cho độ sẵn sàng cấp production.
-   **Lớp Caching:** Lên kế hoạch cụm ElastiCache Redis để quản lý trạng thái phiên (session).
-   **Lưu trữ Đối tượng:** Cấu hình S3 bucket để xử lý tài sản tĩnh (static assets) và lưu trữ tài liệu.

**Đúc kết cốt lõi:**

-   **Vệ sinh Tài chính** dựa trên khả năng quan sát liên tục thông qua Cost Explorer.
-   **Rightsizing Instance** là đòn bẩy tác động cao để giảm chi phí vận hành (OpEx) (lên đến 30-50%).
-   **Sự bền bỉ (Resiliency)** không phải ngẫu nhiên; nó được tạo ra thông qua quy hoạch Multi-AZ có chủ đích.
-   **Năng suất Lập trình viên** được khuếch đại đáng kể nhờ các công cụ phù hợp (AWS Toolkit/CLI).
-   **Đa dạng hóa lưu trữ (Polyglot Persistence)** (dùng đúng DB cho đúng việc) là yếu tố then chốt cho hiệu năng.
-   **Security Group** hoạt động như cơ chế tường lửa có trạng thái (stateful) chính yếu cho chiến lược phòng thủ theo chiều sâu.
