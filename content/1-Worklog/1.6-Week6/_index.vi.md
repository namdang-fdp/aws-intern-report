---
title: "Worklog tuần 6"
date: 2025-10-14
weight: 6
chapter: false
pre: "<b>1.6. </b>"
---

### Mục tiêu tuần 6

-   Làm chủ toàn diện các phân cấp lưu trữ (Storage hierarchy) của AWS: Object Storage và Hybrid Storage.
-   Củng cố kỹ năng phát triển backend thông qua thực hành ngôn ngữ Python.
-   Kết tinh kiến trúc hạ tầng dự án và hoàn thiện mối quan hệ giữa các thành phần.
-   Tiếp thu những hiểu biết tiên tiến về DevSecOps tích hợp Generative AI thông qua webinar chuyên ngành.
-   **Hoàn thiện Workshop:** Triển khai **Lớp Lưu trữ Bền vững** (Persistence Layer - Database & Storage) và cấu hình phân phối tài nguyên tĩnh.

### Nhiệm vụ thực hiện trong tuần

| Ngày | Hoạt động                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                                                                                            |
| ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ------------------------------------------------------------------------------------------------------------- |
| 2    | - **Nghiên cứu sâu về Object Storage:** Phân tích kiến trúc Amazon S3 bucket, đảm bảo độ bền 11 số 9, và cơ chế hosting tĩnh.<br>- **Chiến lược phân tầng:** Phân tích các lớp lưu trữ S3 (Standard, IA) và Amazon Glacier cho lưu trữ lạnh.<br>- **Hoàn thành:** Học phần _Static Website Hosting with Amazon S3_.                                                                                                                                                                       | 14/10/2025   | 15/10/2025      | [AWS S3 Documentation](https://aws.amazon.com/s3/)                                                            |
| 3    | - **Tích hợp Hybrid:** Đánh giá các phương thức AWS Storage Gateway (File, Volume, Tape) để làm cầu nối giữa on-prem và cloud.<br>- **Quản trị chi phí:** Thiết kế các chính sách vòng đời đối tượng (Object Lifecycle Management).<br>- **Thực hành thuật toán:** Rèn luyện thao tác cấu trúc dữ liệu Python và logic xử lý lỗi.<br>- **Tham gia sự kiện:** Tham dự webinar _"Reinventing DevSecOps with AWS Generative AI"_ với diễn giả Hoàng Kha.                                     | 16/10/2025   | 17/10/2025      | [AWS Storage Gateway](https://aws.amazon.com/storagegateway/)<br>[AWS Events](https://aws.amazon.com/events/) |
| 4    | - **Kỹ thuật phục hồi:** Nắm vững các chỉ số RTO/RPO và phương pháp Sao lưu & Khôi phục.<br>- **Bảo vệ dữ liệu:** Triển khai quản trị tập trung sử dụng AWS Backup.<br>- **Thực hành triển khai:** Khởi tạo S3 bucket, triển khai trang web tĩnh và kiểm thử chuyển đổi vòng đời.<br>- **Nghiên cứu DevSecOps:** Tìm hiểu CI/CD pipeline, các công cụ SAST/DAST và bảo mật IaC.<br>- **Thực thi Workshop:** Cấp phát cụm RDS PostgreSQL (Multi-AZ) và ElastiCache Redis chuẩn production. | 18/10/2025   | 19/10/2025      | [AWS Backup](https://aws.amazon.com/backup/), [Workshop 5.6](5-Workshop/5.6-Database-Storage/)                |
| 5    | - **Đóng băng kiến trúc:** Hoàn thiện sơ đồ hạ tầng chi tiết, ánh xạ mọi tương tác thành phần.<br>- **Quản trị mã nguồn:** Tái cấu trúc thư mục repository để phản ánh chuẩn kiến trúc đã chốt.<br>- **Chuẩn hóa:** Thống nhất tech stack và framework để đảm bảo tính nhất quán cho nhóm.<br>- **Phát triển hỗ trợ bởi AI:** Đánh giá **Amazon Q Developer** cho việc sinh mã, kiểm thử đơn vị (unit test) và vá lỗ hổng.                                                                | 20/10/2025   | 21/10/2025      | [Amazon Q Developer](https://aws.amazon.com/q/developer/)                                                     |

### Các khóa học AWS Skill Builder đã hoàn thành

| Khóa học                                | Danh mục    | Trạng thái |
| --------------------------------------- | ----------- | ---------- |
| Static Website Hosting with Amazon S3   | Storage     | ✅         |
| Data Protection with AWS Backup         | Reliability | ✅         |
| Content Delivery with Amazon CloudFront | Networking  | ✅         |

### Kết quả đạt được trong tuần 6

**Năng lực kỹ thuật:**

_Thành thạo Hệ sinh thái Lưu trữ:_

-   **Kiến trúc S3:** Hiểu sâu về cơ chế bucket, đảm bảo độ bền (99.999999999%) và khả năng hosting tĩnh.
-   **Phân tầng dữ liệu:** Làm chủ việc áp dụng các lớp lưu trữ (Storage Classes) dựa trên tần suất truy cập.
-   **Giao diện Hybrid:** Nắm bắt các mô hình tích hợp AWS Storage Gateway để mở rộng lưu trữ đám mây xuống môi trường on-premises.
-   **Tự động hóa tối ưu:** Cấu hình Lifecycle Management để tự động chuyển đổi dữ liệu và giảm thiểu chi phí.

_Đảm bảo hoạt động kinh doanh liên tục (Business Continuity):_

-   **Nền tảng DR:** Nắm vững các chỉ số quan trọng bao gồm **RTO** (Mục tiêu thời gian khôi phục) và **RPO** (Mục tiêu điểm khôi phục).
-   **Sao lưu hợp nhất:** Sử dụng **AWS Backup** để quản lý sao lưu dựa trên chính sách (policy-based) xuyên suốt các dịch vụ AWS.
-   **Chiến lược khôi phục:** Xây dựng các kịch bản khôi phục dữ liệu để đảm bảo tính liên tục của doanh nghiệp.

_Kỷ luật Phát triển & Vận hành:_

-   **Thành thạo Python:** Nâng cao kỹ năng lập trình Python thông qua các bài tập về cấu trúc dữ liệu và xử lý lỗi.
-   **Triển khai thực tế:** Khởi tạo thành công tài nguyên S3, cấu hình chặn truy cập công khai (public access block) và kiểm thử logic hosting.
-   **Quản trị hạ tầng:** Tái cấu trúc phân cấp thư mục mã nguồn để đồng bộ với các tiêu chuẩn kiến trúc.

_DevSecOps & Tích hợp Generative AI:_

-   **Thông tin chuyên ngành:** Thu thập kiến thức thực tế từ webinar _"Reinventing DevSecOps with AWS Generative AI"_ (16/10/2025).
-   **Pipeline bảo mật:** Hiểu rõ việc tích hợp bảo mật vào SDLC sử dụng Jenkins (CI/CD), SonarQube (SAST), OWASP ZAP (DAST), và Terraform (IaC).
-   **Công cụ AI:** Khám phá **Amazon Q Developer** như một trợ lý thông minh để tăng tốc độ bàn giao mã và chủ động quét lỗ hổng bảo mật.

**Tiến độ Workshop - Triển khai Lớp Lưu trữ:**

-   **Cơ sở dữ liệu quan hệ:** Triển khai **RDS PostgreSQL** với cấu hình Multi-AZ trong private subnet để đảm bảo Tính sẵn sàng cao (HA) và tự động failover.
-   **In-Memory Caching:** Cấp phát cụm **ElastiCache Redis** để tối ưu hóa quản lý session và hiệu năng đọc dưới mili-giây.
-   **Lưu trữ đối tượng:** Thiết lập các S3 bucket cho đa dạng mục đích (tài sản tĩnh, người dùng upload, logs).
-   **Tự động hóa chi phí:** Triển khai S3 lifecycle policies để tự động chuyển dữ liệu cũ sang Glacier.
-   **Tích hợp:** Hoàn tất chuỗi kết nối database và endpoint caching để ứng dụng sử dụng.
-   **Bảo vệ dữ liệu:** Đăng ký các tài nguyên lưu trữ quan trọng vào kế hoạch sao lưu của AWS Backup.

**Đúc kết cốt lõi:**

-   **S3** hoạt động như lớp lưu trữ toàn năng; việc chọn đúng Storage Class là đòn bẩy chính để tối ưu chi phí.
-   **Lifecycle Policies** biến việc quản lý dữ liệu thủ công thành cơ chế tiết kiệm chi phí tự động "thiết lập một lần".
-   **DevSecOps** đại diện cho văn hóa "Shift-Left" (dịch chuyển sang trái), nơi bảo mật được nhúng vào mã và pipeline ngay từ đầu chứ không phải kiểm toán ở bước cuối.
-   **RDS Multi-AZ** là yêu cầu bắt buộc cho các workload production đòi hỏi thời gian chết (downtime) tối thiểu.
-   **Caching (Redis)** là phương pháp hiệu quả nhất để tách biệt tải database khỏi lưu lượng đọc lớn của ứng dụng.
-   **Đặt trong Private Subnet** cho database thực thi tư thế bảo mật nghiêm ngặt bằng cách loại bỏ hoàn toàn việc tiếp xúc trực tiếp với internet.
