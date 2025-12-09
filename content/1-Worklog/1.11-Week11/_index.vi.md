---
title: "Worklog tuần 11"
date: 2024-11-18
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11

-   **Tham vấn chiến lược:** Tận dụng kiến thức chuyên sâu từ **AWS Cloud Mastery Series #2** để giải quyết các thách thức phức tạp về ủy quyền (authorization) và quy trình AI.
-   **Hiện đại hóa Frontend:** Thực hiện chuẩn hóa kiến trúc mã nguồn Frontend để nâng cao tính ổn định và khả năng bảo trì.
-   **Mô-đun hóa hạ tầng:** Điều phối tô-pô **Multi-Stack (Đa ngăn xếp)** để tách biệt tài nguyên và tăng tốc quy trình triển khai Serverless.
-   **Tích hợp AI:** Hợp nhất logic CRUD với các pipeline xử lý AI (Xử lý ảnh/Generative AI) sử dụng các mô hình bất đồng bộ.
-   **Ổn định hóa triển khai:** Khắc phục triệt để các điểm nghẽn triển khai dai dẳng, đặc biệt là các bất thường về CORS.
-   **Thực thi Workshop:** Cấp phát **Kiến trúc Dịch vụ AI**, thực thi quản trị Bảo mật/IAM và thiết lập Giám sát/Quan sát.

---

### Nhiệm vụ thực hiện trong tuần

| Ngày    | Hoạt động                                                                                                                                                                                                                                                                                                                                                 | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                                                            |
| :------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------- | :-------------- | :---------------------------------------------------------------------------- |
| CN      | - **Truy vấn kỹ thuật nâng cao:** Trao đổi với các chuyên gia trong **AWS Cloud Mastery Series #2** về các lỗi ủy quyền chi tiết và tối ưu hóa điều phối quy trình AI.                                                                                                                                                                                    | 17/11/2024   | 17/11/2024      | Mentor, AWS Cloud Mastery Series                                              |
| Thứ Hai | - **Quản trị mã nguồn:** Họp nhóm để thống nhất cấu trúc Frontend. <br> - **Phân tích kiến trúc:** Xây dựng chiến lược phân rã `template.yaml` nguyên khối thành các Stack nhỏ hơn theo nghiệp vụ để tối ưu hóa độ trễ `sam deploy`.                                                                                                                      | 18/11/2024   | 18/11/2024      | Tài liệu Kiến trúc Serverless                                                 |
| Thứ Ba  | - **Phân tách Stack:** Cấp phát các CloudFormation Stack cô lập (ví dụ: API Backend Stack, Frontend Hosting Stack). <br> - **Tổng hợp logic AI:** Kết hợp các thao tác CRUD với trigger xử lý AI (Rekognition/S3 events). <br> - **Thực thi Workshop:** Kiến trúc các endpoint API Gateway REST kết hợp với hàng đợi SQS để xử lý payload AI bất đồng bộ. | 19/11/2024   | 19/11/2024      | Mã nguồn Backend, AWS Rekognition, [Workshop 5.7](5-Workshop/5.6-AI-Service/) |
| Thứ Tư  | - **Hồi quy tích hợp:** Chẩn đoán lỗi toàn hệ thống sau khi tích hợp AI, yêu cầu phải gỡ bỏ và triển khai lại toàn bộ stack. <br> - **Kỹ thuật dự phòng:** Triển khai một Multi-Stack dự phòng đã được tối ưu hóa bởi Trưởng nhóm để đảm bảo tính liên tục của việc phát triển.                                                                           | 20/11/2024   | 20/11/2024      | Stack dự phòng của Leader                                                     |
| Thứ Năm | - **Giải quyết chẩn đoán:** Phân tích nguyên nhân gốc rễ các lỗi vi phạm CORS tái diễn. <br> - **Củng cố cấu hình:** Đồng bộ hóa nghiêm ngặt header giữa API Gateway và Lambda. <br> - **Triển khai bảo mật:** Định nghĩa IAM Roles, tích hợp Secrets Manager cho API key và triển khai WAF rules.                                                        | 21/11/2024   | 21/11/2024      | Cấu hình API Gateway/Lambda, [Workshop 5.9](5-Workshop/5.9-Security-IAM/)     |
| Thứ Sáu | - **Ổn định hệ thống:** Đồng bộ nhóm về kiến trúc Frontend mới và chốt cấu hình Stack chính. <br> - **Đóng băng kiến trúc:** Áp dụng chiến lược tách stack để tạo điều kiện cho khả năng mở rộng và bảo trì độc lập trong tương lai.                                                                                                                      | 22/11/2024   | 22/11/2024      | Báo cáo cấu trúc mới                                                          |

---

### Kết quả đạt được trong tuần 11

**Chuyển đổi Kỹ thuật & Tích hợp:**

-   **Đào sâu kiến thức:** Nâng cao sự nhạy bén về serverless thông qua **AWS Cloud Mastery Series**, đặc biệt trong tích hợp Rekognition và xử lý lỗi AuthZ.
-   **Đồng nhất hóa Frontend:** Tái cấu trúc thành công kiến trúc phía client, thiết lập khuôn mẫu nhất quán cho phát triển tương lai.
-   **Vận hành Multi-Stack:** Chuyển đổi từ SAM template nguyên khối sang **kiến trúc Multi-Stack**, giảm đáng kể thời gian triển khai và phạm vi ảnh hưởng lỗi (blast radius).
-   **Khắc phục CORS:** Giải quyết triệt để các bất thường CORS bằng cách căn chỉnh cấu hình lớp Gateway và Application.
-   **Làm chủ triển khai:** Có được kỹ năng xử lý sự cố nâng cao đối với lỗi xác thực SAM Template và lỗi rollback CloudFormation.
-   **Dự phòng kiến trúc:** Thiết lập giao thức "Backup Stack" để duy trì tốc độ dự án trong quá trình tái cấu trúc kiến trúc lớn.
-   **Chuyển giao giai đoạn:** Đưa dự án thành công vào giai đoạn **Kiểm thử chức năng AI** với khung xử lý sự cố vững chắc.

**Tiến độ Workshop - Kiến trúc AI, Bảo mật & Khả năng quan sát:**

-   **Điều phối API:** Cấu hình API Gateway REST API với các endpoint chuyên dụng (`/writing/evaluate`, `/speaking/evaluate`, `/flashcard/generate`).
-   **Tách biệt bất đồng bộ:** Cấp phát **SQS queues** (writing, speaking, flashcard) để đệm yêu cầu và tách biệt API khỏi lớp tính toán.
-   **Compute & AI:** Triển khai Lambda functions (`writing_evaluator`, `speaking_evaluator`, `rag_flashcard`) tích hợp **Amazon Bedrock** và **Google Gemini API**.
-   **Lưu trữ NoSQL:** Cấu hình bảng DynamoDB để lưu trữ kết quả đánh giá và bộ flashcard được tạo ra.
-   **Quản lý bí mật:** Tích hợp **AWS Secrets Manager** để xoay vòng và tiêm (inject) API key an toàn tại runtime.
-   **Tư thế bảo mật:**
    -   Thực thi quyền truy cập **Đặc quyền tối thiểu (Least-Privilege)** thông qua IAM Roles chi tiết.
    -   Triển khai **AWS WAF** Web ACLs để phòng thủ ở lớp ứng dụng.
-   **Khả năng quan sát:** Kích hoạt **CloudWatch Logs & Alarms** để theo dõi lỗi và **CloudWatch Insights** để phân tích log chuyên sâu.

**Đúc kết cốt lõi:**

-   **Tách biệt (Decoupling) là chìa khóa:** Chia nhỏ ứng dụng nguyên khối thành Multi-Stack cải thiện tốc độ triển khai và khả năng quản lý.
-   **Async cho AI:** Các tiến trình AI thường chậm; sử dụng SQS cho phép API phản hồi ngay lập tức trong khi Lambda xử lý nền (Kiến trúc hướng sự kiện).
-   **Bảo mật ưu tiên:** Không bao giờ hardcode API key; Secrets Manager là bắt buộc cho bảo mật cấp production.
-   **Khả năng quan sát:** CloudWatch Alarms là thiết yếu để phát hiện Lambda timeout hoặc throttling trước khi người dùng báo cáo.
