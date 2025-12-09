---
title: "Work log tuần 12"
date: 2024-11-25
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Mục tiêu tuần 12

-   **Hoàn thiện Chức năng:** Đạt 100% tiến độ các thao tác CRUD và pipeline xử lý ảnh bằng AI (bao gồm cả logic Cập nhật).
-   **Tính kiên cường Kiến trúc:** Tái cấu trúc quy trình xử lý ảnh sử dụng **Amazon SQS** để giới thiệu cơ chế tách biệt bất đồng bộ và đệm tải.
-   **Đồng bộ Tính năng:** Hoàn tất các khả năng phụ trợ bao gồm Củng cố bảo mật, Tích hợp địa lý (Map Pinning), và Thông báo SNS.
-   **Sẵn sàng Trình bày:** Trau chuốt UX/UI Frontend, lên chiến lược sở hữu tên miền, và xác thực bản build cuối cùng thông qua **AWS Cloud Mastery Series**.

---

### Nhiệm vụ thực hiện trong tuần

| Ngày    | Hoạt động                                                                                                                                                                                                                                                                                               | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                         |
| :------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----------- | :-------------- | :----------------------------------------- |
| Thứ Hai | - **Ổn định hóa Mã nguồn:** Loại bỏ các lỗi tồn đọng trong chức năng Update và tích hợp AI (cụ thể là trích xuất Sub ID và logic Rekognition) để đảm bảo tính toàn vẹn chức năng.                                                                                                                       | 25/11/2024   | 25/11/2024      | Hướng dẫn của Mentor, Mã nguồn Backend     |
| Thứ Ba  | - **Tách biệt Bất đồng bộ:** Tiêm (Inject) **AWS SQS** vào pipeline AI để đệm các yêu cầu, kích hoạt Kiến trúc Hướng sự kiện (Event-Driven Architecture) có khả năng mở rộng. <br> - **Định nghĩa Luồng:** Ánh xạ lại đường dẫn nhập liệu: Upload -> S3 Event -> SQS -> Lambda (AI Worker) -> DynamoDB. | 26/11/2024   | 26/11/2024      | Tài liệu AWS SQS, Kiến trúc Lambda         |
| Thứ Tư  | - **Hoàn thiện UX/UI:** Hoàn tất phát triển các giao diện Frontend cốt lõi (Bảng điều khiển, Xem chi tiết, Hồ sơ người dùng). <br> - **Tích hợp Địa lý:** Triển khai logic **Ghim bản đồ (Map Pinning)** bằng cách lưu trữ và hiển thị tọa độ địa lý từ DynamoDB.                                       | 27/11/2024   | 27/11/2024      | Mã nguồn Frontend, DynamoDB Geo            |
| Thứ Năm | - **Củng cố Bảo mật:** Tinh chỉnh IAM Policy và Cognito claims để đảm bảo truy xuất chính xác `Sub` ID cho việc ủy quyền sở hữu tài nguyên. <br> - **Hệ thống Thông báo:** Tích hợp **AWS SNS** để kích hoạt thông báo đẩy (push notifications) khi bài đăng được xử lý thành công.                     | 28/11/2024   | 28/11/2024      | Tài liệu AWS SNS, Cognito/IAM              |
| Thứ Sáu | - **Xác thực Chuyên gia:** Tham dự buổi **AWS Cloud Mastery Series** cuối cùng để rà soát trước demo và chốt kiến trúc. <br> - **Chiến lược DNS:** Chốt lựa chọn tên miền và chuẩn bị các hosted zone trên Route 53 cho việc chuyển đổi sang production.                                                | 29/11/2024   | 29/11/2024      | Mentor, AWS Cloud Mastery Series, Route 53 |

---

### Kết quả đạt được trong tuần 12

**Độ trưởng thành Hệ thống & Sẵn sàng Demo:**

-   **Cột mốc Chức năng:** Đạt **100% hoàn thành** các tính năng CRUD cốt lõi và Xử lý ảnh AI, mang lại một backend ổn định và phản hồi nhanh.
-   **Nâng cấp Kiến trúc:** Triển khai thành công **Kiến trúc Hướng sự kiện** sử dụng SQS, tách biệt lớp nhập liệu khỏi lớp xử lý để tăng cường độ tin cậy.
-   **Hoàn thiện Tính năng:** Đã phát hành các cải tiến quan trọng bao gồm Củng cố AuthZ, Trực quan hóa địa lý (Map Pinning), và Thông báo sự kiện (SNS).
-   **Trau chuốt Frontend:** Đã bàn giao Giao diện Người dùng sẵn sàng cho trình bày với các luồng người dùng được hiện thực hóa đầy đủ.
-   **Đồng bộ Chiến lược:** Đã xác thực kiến trúc giải pháp cuối cùng thông qua **AWS Cloud Mastery Series**, đảm bảo tuân thủ các thực hành tốt nhất (best practices).
-   **Chuẩn bị Go-Live:** Hoàn tất nghiên cứu tên miền và quy hoạch DNS cho việc ra mắt công khai.
-   **Trạng thái:** Dự án đã chính thức đạt trạng thái **Sẵn sàng Demo (Demo Readiness)**, chuẩn bị cho buổi trình bày và đánh giá cuối cùng.
