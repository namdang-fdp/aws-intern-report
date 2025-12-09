---
title: "Worklog tuần 2"
date: 2025-09-15
weight: 2
chapter: false
pre: "<b>1.2. </b>"
---

### Mục tiêu tuần 2

-   **Năng lực cốt lõi:** Đạt được sự thành thạo về vận hành Amazon EC2 và các nguyên lý VPC (Module 2).
-   **Cấp phát hạ tầng:** Kiến trúc và cấu hình các thành phần mạng thiết yếu để triển khai compute.
-   **Khám phá DNS:** Bắt đầu nghiên cứu về Amazon Route 53 và các mô hình quản lý tên miền.
-   **Kết nối ngành:** Thu thập thông tin chiến lược về AI và Dữ liệu thông qua sự kiện **Cloud Day**.

### Nhiệm vụ thực hiện trong tuần

| Ngày | Hoạt động                                                                                                                                                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                                                                                                             |
| ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| 2    | - **Phân tích Kiến trúc Mạng:** Nghiên cứu sâu về tô-pô VPC và các thành phần mạng.<br>- **Nguyên lý Kiến trúc:** Tiếp thu các mẫu thiết kế (design patterns) thông qua bài giảng nâng cao của Mentor Gia Hưng.<br>- **Hoàn thành:** Học phần _Networking Essentials with Amazon VPC_.                                      | 15/09/2025   | 16/09/2025      | [AWS VPC Documentation](https://docs.aws.amazon.com/vpc/)                                                                      |
| 3    | - **Triển khai Hạ tầng:** Cấp phát tài nguyên VPC bao gồm Subnets và Gateways.<br>- **Khởi chạy Compute:** Triển khai EC2 instance trong môi trường mạng đã cấu hình.<br>- **Phân lớp Bảo mật:** Phân tích và thực thi Security Groups và Network ACLs.<br>- **Hoàn thành:** Học phần _Compute Essentials with Amazon EC2_. | 16/09/2025   | 17/09/2025      | [AWS EC2 Documentation](https://docs.aws.amazon.com/ec2/) <br> [Introduction to Amazon EC2](https://000004.awsstudygroup.com/) |
| 4    | - **Xử lý sự cố vận hành:** Giải quyết các điểm nghẽn xác thực tài khoản thông qua quy trình xác minh tài liệu.<br>- **Tối ưu hóa hỗ trợ:** Làm chủ quy trình yêu cầu hỗ trợ (support ticket).<br>- **Hoàn thành:** Các học phần _Creating Your First AWS Account_ và _Getting Help with AWS Support_.                      | 17/09/2025   | 20/09/2025      | [AWS Support](https://aws.amazon.com/support/) <br>[Request Support with AWS Support](https://000009.awsstudygroup.com/)       |
| 5    | - **Kết nối Chiến lược:** Tham dự **Cloud Day** để giao lưu với cộng đồng công nghệ.<br>- **Phân tích Xu hướng:** Tiếp thu các bước tiến quan trọng trong Kỹ thuật AI và Dữ liệu.<br>- **Mentorship:** Kết nối với các nhân vật nổi bật trong hệ sinh thái AWS.                                                             | 18/09/2025   | 18/09/2025      | Cloud Day Event                                                                                                                |

### Các khóa học AWS Skill Builder đã hoàn thành

| Khóa học                                  | Danh mục        | Trạng thái |
| ----------------------------------------- | --------------- | ---------- |
| Creating Your First AWS Account           | Getting Started | ✅         |
| Managing Costs with AWS Budgets           | Cost Management | ✅         |
| Getting Help with AWS Support             | Support         | ✅         |
| Access Management with AWS IAM            | Security        | ✅         |
| Networking Essentials with Amazon VPC     | Networking      | ✅         |
| Compute Essentials with Amazon EC2        | Compute         | ✅         |
| Instance Profiling with IAM Roles for EC2 | Security        | ✅         |

### Kết quả đạt được trong tuần 2

**Năng lực kỹ thuật:**

_Kỹ thuật IaaS & Mạng:_

-   **Làm chủ VPC:** Đạt được sự hiểu biết toàn diện về kiến trúc Virtual Private Cloud.
-   **Điều phối Tài nguyên:** Cấp phát thành công ngăn xếp mạng (network stack) hoàn chỉnh cho EC2:
    -   **Phân đoạn mạng:** Cấu hình **Subnets** chi tiết để cô lập logic.
    -   **Kết nối biên:** Thiết lập **Internet Gateway** cho truy cập bên ngoài.
    -   **Quản trị lưu lượng:** Định nghĩa **Route Tables** để kiểm soát chặt chẽ luồng gói tin.
    -   **Tường lửa Instance:** Triển khai **Security Groups** để lọc lưu lượng có trạng thái (stateful).
-   **Tích hợp Danh tính:** Tận dụng **IAM Roles** và instance profiles để bảo mật thông tin đăng nhập EC2.
-   **Rào chắn Tài chính:** Triển khai các chiến lược quản lý chi phí sử dụng AWS Budgets.

**Thông tin Chiến lược (Cloud Day):**

-   **Hội nhập Cộng đồng:** Kết nối thành công với các mentor AWS và chuyên gia trong ngành.
-   **Thông tin Thị trường:** Có được cái nhìn quan trọng về quỹ đạo phát triển của công nghệ AI và Dữ liệu.
-   **Sẵn sàng cho Tương lai:** Kiểm chứng nhu cầu thị trường ngày càng tăng đối với các giải pháp đám mây tích hợp AI.

**Đúc kết cốt lõi:**

-   **VPC** là nền tảng bất di bất dịch của mạng AWS; thiết kế của nó quyết định tính bảo mật và khả năng kết nối.
-   **Security Groups** hoạt động như tuyến phòng thủ đầu tiên (tường lửa ảo) ở cấp độ compute.
-   **IAM Roles** là thiết yếu cho kiến trúc "Không thông tin đăng nhập" (Credential-less), loại bỏ việc hardcode bí mật trong mã nguồn.
-   **Giám sát chủ động** thông qua AWS Budgets là bước đầu tiên trong Quản lý Tài chính Đám mây (FinOps).
