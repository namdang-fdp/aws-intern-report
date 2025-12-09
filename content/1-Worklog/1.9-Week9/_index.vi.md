---
title: "Worklog tuần 9"
date: 2024-11-04
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9

-   **Chuyển đổi Framework:** Thực hiện chuyển đổi toàn diện quy trình phát triển sang **AWS SAM (Serverless Application Model)**.
-   **Hiện đại hóa kiến trúc:** Tái cấu trúc logic CRUD để phù hợp với các mô hình serverless chuẩn của SAM.
-   **Chuẩn hóa môi trường:** Khắc phục các sai lệch về môi trường runtime cục bộ để đạt được trạng thái triển khai thành công trên cloud.
-   **Container hóa:** Tích hợp **Docker** để chuẩn hóa quy trình build và quản lý thư viện phụ thuộc.
-   **Thực thi Workshop:** Điều phối việc triển khai các vi dịch vụ (microservices) Frontend và Backend đã container hóa thông qua **Amazon ECS**.

---

### Nhiệm vụ thực hiện trong tuần

| Ngày    | Hoạt động                                                                                                                                                                                                                                                                                                                                                                                                  | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                                                       |
| :------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------- | :-------------- | :----------------------------------------------------------------------- |
| Thứ Hai | - **Phân tích AWS SAM:** Mổ xẻ cấu trúc `template.yaml`, các lệnh SAM CLI và cơ chế hoạt động giữa Lambda và API Gateway. <br> - **Lộ trình chuyển đổi:** Xây dựng chiến lược chuyển đổi các Lambda function cũ sang cấu trúc SAM. <br> - **Giả lập cục bộ:** Đánh giá khả năng kiểm thử cục bộ thông qua `sam local invoke`.                                                                              | 04/11/2024   | 04/11/2024      | AWS SAM Documentation, AWS Study Group                                   |
| Thứ Ba  | - **Hiện đại hóa mã nguồn:** Tái thiết kế các handler Create/Read để tận dụng nguồn sự kiện của SAM. <br> - **Chiến lược Container:** Cấu hình **Docker** để đảm bảo sự nhất quán của Python runtime trong quá trình `sam build`. <br> - **Quản lý Layer:** Xây dựng Dockerfile cho các dependency layer của Lambda. <br> - **Thực thi Workshop:** Cấp phát các ECR repository để quản lý image container. | 05/11/2024   | 06/11/2024      | Docker Documentation, SAM CLI, [Workshop 5.4](5-Workshop/5.4-ECS-Setup/) |
| Thứ Tư  | - **Mô phỏng cục bộ:** Thực hiện unit test thông qua việc gọi hàm cục bộ. <br> - **Sai lệch môi trường:** Xác định các điểm nghẽn nghiêm trọng trong giả lập cục bộ (Xung đột thư viện, sai lệch phiên bản Python, lỗi kết nối DynamoDB local). <br> - **Xử lý sự cố:** Nỗ lực tái cấu hình để đồng bộ môi trường local và remote.                                                                         | 06/11/2024   | 07/11/2024      | SAM CLI Error Reports, Stack Overflow                                    |
| Thứ Năm | - **Thay đổi chiến lược:** Quyết định áp dụng chiến lược **"Cloud-First Verification"** (Triển khai trước, kiểm thử sau) để vượt qua các hạn chế giả lập cục bộ. <br> - **Tối ưu hóa Template:** Tinh chỉnh định nghĩa trong `template.yaml`, chính sách IAM và biến môi trường. <br> - **Xác thực:** Kiểm tra cú pháp template và sự phụ thuộc tài nguyên.                                                | 07/11/2024   | 08/11/2024      | CloudFormation Template Validator                                        |
| Thứ Sáu | - **Triển khai Production:** Thực thi thành công `sam deploy --guided` để cấp phát stack lên AWS. <br> - **Kiểm chứng Endpoint:** Xác minh tính toàn vẹn của API và hoạt động CRUD qua Postman/cURL. <br> - **Tài liệu hóa:** Chuẩn hóa quy trình triển khai để nhóm áp dụng. <br> - **Thực thi Workshop:** Điều phối triển khai ECS Fargate (Task Definitions, tạo Service và đẩy Image).                 | 08/11/2024   | 08/11/2024      | AWS CloudFormation Logs, [Workshop 5.4](5-Workshop/5.4-ECS-Setup/)       |

---

### Kết quả đạt được trong tuần 9

**Chuyển đổi Kỹ thuật:**

-   **Chuyển đổi Framework thành công:** Hoàn tất việc chuyển đổi chiến lược sang **AWS SAM**, thiết lập Cơ sở hạ tầng dưới dạng mã (IaC) cho tài nguyên serverless.
-   **Tái cấu trúc kiến trúc:** Hiện đại hóa thành công các CRUD handler thành cấu trúc module SAM.
-   **Giải quyết phụ thuộc:** Tận dụng **Docker** để thực thi tính nhất quán khi build, loại bỏ các lỗi "chạy được trên máy tôi".
-   **Đột phá trong triển khai:** Vượt qua các hạn chế debug cục bộ bằng cách chuyển sang quy trình kiểm chứng trên cloud, dẫn đến lần triển khai API trực tiếp thành công đầu tiên.
-   **Cột mốc:** API của **Bandup IELTS** hiện đã hoạt động trên môi trường cloud thực tế.
-   **Quản trị:** Thiết lập quy trình triển khai có thể lặp lại và một file `template.yaml` đóng vai trò là nguồn sự thật duy nhất (single source of truth).

**Tiến độ Workshop - Điều phối ECS & Container:**

-   **Quản lý tài sản (Artifact):** Thiết lập ECR repositories cho Frontend (Next.js) và Backend (Spring Boot).
-   **Build Pipeline:** Thực thi build và push Docker image với chiến lược gắn thẻ (tagging) ngữ nghĩa.
-   **Đặc tả tác vụ (Task Spec):** Định nghĩa chi tiết ECS Task Definitions (Frontend: 0.5 vCPU/1GB, Backend: 1 vCPU/2GB).
-   **Điều phối cụm:** Cấp phát ECS Cluster tận dụng các capacity provider của Fargate.
-   **Tính sẵn sàng cao (HA):** Triển khai ECS Services theo cấu hình Active-Passive Multi-AZ (2 active replicas, 1 standby).
-   **Service Mesh:** Cấu hình **Service Connect** để khám phá dịch vụ nội bộ liền mạch.
-   **Khả năng phục hồi:** Triển khai health checks tự động để tự phục hồi tác vụ.

**Đúc kết cốt lõi:**

-   **Sức mạnh IaC:** SAM đơn giản hóa sự phức tạp của serverless bằng cách coi hạ tầng là mã.
-   **Tính nhất quán của Container:** Docker là yếu tố bắt buộc để đảm bảo môi trường build nhất quán trên các máy phát triển khác nhau.
-   **Thích ứng chiến lược:** Nhận biết khi nào nên từ bỏ giả lập cục bộ để chuyển sang kiểm thử trên cloud là một kỹ năng DevOps quan trọng.
-   **Độ chính xác IAM:** SAM template thực thi các ranh giới quyền hạn nghiêm ngặt, rất quan trọng cho việc thực thi Lambda an toàn.
-   **Trừu tượng hóa Fargate:** ECS Fargate loại bỏ gánh nặng vận hành quản lý các EC2 instance cho container.
-   **Service Connect:** Đơn giản hóa giao tiếp microservice nội bộ, giảm nhu cầu sử dụng các bộ cân bằng tải nội bộ phức tạp.
