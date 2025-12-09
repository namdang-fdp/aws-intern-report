---
title: "Worklog tuần 8"
date: 2024-10-28
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8

-   **Cột mốc học thuật:** Hoàn thành tốt kỳ thi giữa kỳ (ngày 31/10) với kết quả khả quan.
-   **Khởi tạo Backend:** Bắt đầu phát triển các logic **CRUD (Create, Read, Update, Delete)** cốt lõi cho hệ sinh thái **Bandup IELTS**.
-   **Chiến lược Serverless:** Kiến trúc việc tích hợp các **dịch vụ AWS Serverless** (Lambda, API Gateway, DynamoDB) vào tô-pô dự án.
-   **Cấp phát môi trường:** Thiết lập môi trường phát triển cục bộ (local) vững chắc và khung sườn dự án.

---

### Nhiệm vụ thực hiện trong tuần

| Ngày    | Hoạt động                                                                                                                                                                                                                                                                                                                                | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                        |
| :------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------- | :-------------- | :---------------------------------------- |
| Thứ Hai | - **Tổng hợp kiến thức tiền kỳ thi:** Thực hiện rà soát kiến thức lần cuối. Ôn tập các điểm khác biệt kiến trúc (IAM Policies vs Roles, Các lớp bảo mật, Logic định tuyến VPC). <br> - **Mô phỏng:** Tối ưu hóa chiến lược quản lý thời gian cho bối cảnh phòng thi.                                                                     | 28/10/2024   | 28/10/2024      | Personal notes, AWS Builders              |
| Thứ Ba  | - **Kỹ thuật môi trường:** Cấu hình chuỗi công cụ (toolchain) bao gồm môi trường Python, xác thực AWS CLI và các tiện ích mở rộng IDE. <br> - **Sẵn sàng:** Đảm bảo sự chuẩn bị tốt nhất về cả tinh thần và kỹ thuật cho bài đánh giá sắp tới.                                                                                           | 29/10/2024   | 30/10/2024      | AWS CLI Documentation                     |
| Thứ Tư  | - **Thực hiện bài đánh giá:** Tham gia **Kỳ thi giữa kỳ** vào ngày 31/10. <br> - **Hồi tưởng (Retrospective):** Phân tích sau kỳ thi để xác định các điểm mạnh và các mảng lý thuyết cần củng cố thêm.                                                                                                                                   | 31/10/2024   | 31/10/2024      | Địa điểm thi                              |
| Thứ Năm | - **Xây dựng nguyên mẫu Serverless:** Thiết kế vector **'Create'** (Tạo mới) đầu tiên cho mô-đun Flashcard. <br> - **Compute & Storage:** Triển khai thử nghiệm các hàm **AWS Lambda** và thiết kế lược đồ **DynamoDB** cho truy xuất dữ liệu hiệu năng cao.                                                                             | 01/11/2024   | 01/11/2024      | Tài liệu AWS Lambda & DynamoDB            |
| Thứ Sáu | - **Điều phối API:** Thiết kế giao diện RESTful thông qua **API Gateway**. <br> - **Kiến trúc luồng dữ liệu:** Ánh xạ đường đi của dữ liệu (Ingress/Egress): Frontend → API Gateway → Lambda → DynamoDB. <br> - **Triển khai Logic:** Lập trình trình xử lý (handler) **'Read'** để truy xuất bộ dữ liệu flashcard từ kho lưu trữ NoSQL. | 02/11/2024   | 02/11/2024      | Tài liệu API Gateway, Serverless patterns |

---

### Kết quả đạt được trong tuần 8

**Tiến độ Học thuật & Kỹ thuật:**

-   **Thành tựu học thuật:** Đã hoàn thành giai đoạn thi giữa kỳ (31/10), kiểm chứng nền tảng kiến thức đã tích lũy.
-   **Sẵn sàng cho DevOps:** Đã cấp phát đầy đủ môi trường phát triển, tích hợp Python và AWS CLI cho quy trình làm việc trơn tru.
-   **Logic Backend:** Đã triển khai các vi chức năng **Create/Read** đầu tiên cho **Bandup IELTS** sử dụng kiến trúc serverless.
-   **Bản thiết kế kiến trúc:** Đã xác thực bộ ba Serverless cho dự án:
    -   **API Gateway** đóng vai trò điểm nhập HTTP an toàn.
    -   **Lambda** thực thi logic nghiệp vụ theo hướng sự kiện.
    -   **DynamoDB** cung cấp khả năng lưu trữ NoSQL độ trễ thấp.
-   **Đào sâu năng lực:** Củng cố chuyên môn về các thành phần serverless quan trọng cho phát triển ứng dụng hiện đại.
-   **Quản trị dự án:** Thiết lập cấu trúc thư mục dự án gọn gàng để hỗ trợ khả năng mở rộng trong tương lai.
-   **Bàn giao mã nguồn:** Đã hoàn thành Lambda handler chức năng đầu tiên để nhập liệu.

**Đúc kết cốt lõi:**

-   **Hiệu quả vận hành:** Kiến trúc Serverless trừu tượng hóa việc quản lý hạ tầng, giảm thiểu đáng kể gánh nặng vận hành.
-   **Mở rộng hướng sự kiện:** Lambda function cung cấp khả năng tự động mở rộng (auto-scaling) được kích hoạt bởi các sự kiện yêu cầu cụ thể.
-   **Hiệu năng:** DynamoDB mang lại độ trễ mili-giây một chữ số ổn định cho các workload thông lượng cao.
-   **Mô hình Gateway:** API Gateway hoạt động như trình điều phối trung tâm cho quản lý API, bảo mật và điều tiết lưu lượng.
-   **Khung sườn (Scaffolding):** Thiết lập cấu trúc dự án đúng đắn ngay từ đầu là yếu tố then chốt cho khả năng bảo trì lâu dài.
