---
title: "Worklog tuần 10"
date: 2024-11-11
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu tuần 10

-   **Ổn định hóa môi trường:** Củng cố quy trình triển khai AWS SAM/Serverless và giải quyết dứt điểm các yếu tố gây mất ổn định nghiêm trọng.
-   **Giải quyết chẩn đoán:** Gỡ lỗi hệ thống các điểm nghẽn tương tác, đặc biệt là lỗi cấu hình CORS và lỗi xác thực template.
-   **Tích hợp Full-Stack:** Hợp nhất lớp Frontend và Backend để kích hoạt kiểm thử End-to-End (E2E) trên giao diện người dùng.
-   **Kiểm chứng CRUD:** Hoàn thiện và xác thực logic **Read** và **Delete** với cơ chế xử lý lỗi mạnh mẽ.
-   **Tham vấn chuyên gia:** Tận dụng kiến thức từ **AWS Cloud Mastery Series** để giải quyết các rào cản kiến trúc.
-   **Thực thi Workshop:** Kiến trúc lớp Ingress sử dụng **Application Load Balancer (ALB)** để phân phối lưu lượng thông minh.

---

### Nhiệm vụ thực hiện trong tuần

| Ngày    | Hoạt động                                                                                                                                                                                                                                                                                                                                         | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                                                         |
| :------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----------- | :-------------- | :------------------------------------------------------------------------- |
| Thứ Hai | - **Khắc phục CORS:** Đồng bộ hóa cấu hình preflight (OPTIONS) trên **API Gateway** với header phản hồi của Lambda để cấp quyền truy cập cho Frontend. <br> - **Làm sạch Template:** Tái cấu trúc `template.yaml` để giải quyết các phụ thuộc vòng lặp và ngăn chặn lỗi xác thực khi `sam deploy`.                                                | 11/11/2024   | 11/11/2024      | Tài liệu API Gateway/CORS                                                  |
| Thứ Ba  | - **Tối ưu hóa truy vấn:** Củng cố hàm **Read** để đảm bảo truy vấn DynamoDB chính xác và định dạng JSON payload chuẩn hóa. <br> - **Tính kiên cường:** Triển khai xử lý ngoại lệ cho các tập dữ liệu rỗng và tham số truy vấn không hợp lệ. <br> - **Khả năng quan sát:** Chèn log cấu trúc để phục vụ gỡ lỗi runtime.                           | 12/11/2024   | 12/11/2024      | Tài liệu truy vấn DynamoDB                                                 |
| Thứ Tư  | - **Tích hợp Client:** Hợp nhất mã nguồn Frontend với API đã triển khai để kiểm chứng việc render dữ liệu. <br> - **Xác minh UI:** Hiển thị thành công danh sách flashcard trên các component React/Vue. <br> - **Thực thi Workshop:** Cấp phát Application Load Balancer (ALB) trong public subnet và ánh xạ Target Groups.                      | 13/11/2024   | 13/11/2024      | Tài liệu Frontend Framework, [Workshop 5.5](5-Workshop/5.5-Load-Balancer/) |
| Thứ Năm | - **Triển khai Logic Delete:** Phát hành chức năng xóa tài nguyên. <br> - **Điểm nghẽn Ủy quyền:** Phát hiện lỗi nghiêm trọng trong việc trích xuất **Cognito User Sub ID** từ JWT token trong Lambda, gây chặn các thao tác đặc quyền. <br> - **Điều tra:** Khởi động quy trình gỡ lỗi sâu luồng xác thực (authentication flow).                 | 14/11/2024   | 14/11/2024      | Tài liệu AWS Cognito                                                       |
| Thứ Sáu | - **Cố vấn chiến lược:** Tham dự **AWS Cloud Mastery Series** để tiếp thu góc nhìn chuyên gia về Serverless patterns và Best practices cho AuthZ. <br> - **Chiến lược khắc phục:** Áp dụng hướng dẫn của mentor để tái cấu trúc logic phân tích Cognito token. <br> - **Cơ sở tri thức:** Tài liệu hóa các bước giải quyết để tham khảo cho nhóm. | 15/11/2024   | 15/11/2024      | Mentor, AWS Cloud Mastery Series                                           |

---

### Kết quả đạt được trong tuần 10

**Ổn định Kỹ thuật & Tích hợp:**

-   **Giải quyết Cấu hình:** Khắc phục thành công lỗi CORS dai dẳng và ổn định vòng lặp triển khai SAM, đảm bảo luồng CI/CD tin cậy.
-   **Đồng bộ Chuyên gia:** Thu thập được định hướng kiến trúc quan trọng từ **AWS Cloud Mastery Series**, giải quyết trực tiếp các vấn đề của dự án.
-   **Kết nối E2E:** Đạt được cột mốc **Tích hợp Frontend-Backend** thành công đầu tiên, cho phép kiểm thử chức năng trên UI.
-   **Vận hành CRUD:** Triển khai thành công các thao tác **Read** và **Delete**, hiện đã hoạt động trên giao diện web.
-   **Nhận diện Điểm nghẽn:** Xác định chính xác các lỗi ủy quyền (Authorization failures):
    -   **Trích xuất Ngữ cảnh:** Lambda không thể phân tích chính xác **Cognito Sub ID** từ header xác thực.
    -   **Chặn phụ thuộc:** Các hàm Update/Delete bị đình trệ do yêu cầu xác minh danh tính nghiêm ngặt.
-   **Giai đoạn Kiểm thử:** Đưa dự án vào giai đoạn Kiểm thử Chấp nhận Người dùng (UAT) cho các thao tác cơ bản.
-   **Chuẩn hóa Quy trình:** Thiết lập các giao thức gỡ lỗi và tiêu chuẩn xử lý lỗi cho đội ngũ phát triển.

**Tiến độ Workshop - Cấu hình Load Balancer:**

-   **Kiến trúc Ingress:** Cấp phát Application Load Balancer (ALB) trải dài trên hai Availability Zones (Public Subnets).
-   **Định tuyến Lưu lượng:** Cấu hình Target Groups cho các dịch vụ ECS (Frontend: 3000, Backend: 8080).
-   **Giám sát Sức khỏe:** Triển khai health checks tự động để loại bỏ các target không khỏe mạnh.
-   **Giảm tải Bảo mật:** Cấu hình **SSL/TLS termination** sử dụng chứng chỉ ACM để giảm tải gánh nặng mã hóa cho backend.
-   **Tích hợp DNS:** Ánh xạ endpoint ALB tới Route 53 để phân giải tên miền.
-   **Định tuyến theo Đường dẫn:** Định nghĩa quy tắc listener để phân tách lưu lượng (Frontend: `/`, Backend: `/api/*`).
-   **An ninh Mạng:** Áp dụng quy tắc security group cho phép luồng lưu lượng ALB-to-ECS nghiêm ngặt.

**Đúc kết cốt lõi:**

-   **Sự phức tạp của CORS:** Việc tuân thủ CORS đòi hỏi cấu hình đồng bộ trên cả hai lớp Gateway (Preflight) và Application (Headers).
-   **Ngữ cảnh Định danh:** Raw JWT tokens phải được giải mã tỉ mỉ để trích xuất **User Sub ID** phục vụ cho việc ủy quyền chi tiết.
-   **Tuân thủ Hợp đồng:** Sự tích hợp thành công phụ thuộc vào việc tuân thủ nghiêm ngặt các hợp đồng API (API contracts) và định dạng tuần tự hóa dữ liệu giữa Client và Server.
-   **Khả năng quan sát:** Logging toàn diện là biện pháp phòng thủ duy nhất chống lại các lỗi runtime khó hiểu trên production.
-   **Hiệu quả của ALB:** Application Load Balancer cung cấp trí thông minh quan trọng (Định tuyến theo đường dẫn) và lợi ích hiệu năng (SSL Offloading) cho các workload container.
