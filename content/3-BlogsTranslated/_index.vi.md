---
title: "Các bài blogs đã dịch"
date: 2025-09-09
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

Chào mừng đến với thư viện các bài viết kỹ thuật chuyên sâu đã được biên dịch. Tại đây, tôi tập trung giới thiệu các giải pháp thực tiễn xoay quanh ba trụ cột chính: **Bảo mật đám mây (Cloud Security)**, **Toàn vẹn dữ liệu (Data Integrity)** và **Tối ưu hóa vận hành (Operational Excellence)**.

Dưới đây là danh sách các bài blog nổi bật:

### [Blog 1 - Cách sử dụng AWS Transfer Family và GuardDuty để bảo vệ khỏi phần mềm độc hại](3.1-Blog1/)

Trong bối cảnh chia sẻ tệp tin qua môi trường công cộng ngày càng phổ biến, bài viết này giới thiệu một kiến trúc bảo mật **Serverless** toàn diện. Giải pháp kết hợp sức mạnh của **AWS Transfer Family** (SFTP) và **Amazon GuardDuty** để tự động hóa quy trình quét mã độc. Bạn sẽ khám phá cách xây dựng một luồng công việc (workflow) thông minh giúp phát hiện, cách ly các tệp tin nguy hại và gửi cảnh báo tức thì cho người dùng mà không cần gánh nặng quản lý hạ tầng máy chủ hay cập nhật chữ ký virus thủ công.

### [Blog 2 - Ngăn chặn việc mã hóa ngoài ý muốn đối với các đối tượng trong Amazon S3](3.2-Blog2/)

Một bài phân tích sâu sắc về kỹ thuật tấn công nơi kẻ xấu lợi dụng thông tin xác thực bị lộ để mã hóa dữ liệu S3 bằng khóa SSE-C, tạo ra kịch bản tương tự ransomware. Bài viết không chỉ dừng lại ở việc cảnh báo mà còn cung cấp bộ **4 thực hành bảo mật cốt lõi** để xây dựng lớp phòng thủ vững chắc: Chiến lược sử dụng thông tin xác thực ngắn hạn, Quy trình khôi phục dữ liệu (Versioning, Replication), Giám sát tài nguyên chủ động, và các Chính sách kiểm soát (Policies) để chặn đứng nguy cơ từ trứng nước.

### [Blog 3 - Hướng dẫn dành cho Nhà phát triển Game về Amazon DocumentDB — Phần 3: Các thực tiễn tốt nhất trong vận hành](3.3-Blog3/)

Đây là cẩm nang không thể thiếu cho các kỹ sư dữ liệu và nhà phát triển Game, tập trung vào việc đưa **Amazon DocumentDB** vào môi trường sản xuất (Production). Bài viết đi sâu vào các khía cạnh kỹ thuật then chốt:

-   **Bảo mật:** Thiết lập mã hóa và kiểm soát truy cập (RBAC) chặt chẽ.
-   **Mở rộng (Scaling):** Chiến lược cân bằng tải đọc/ghi và quản lý kết nối thông minh.
-   **Giám sát (Observability):** Tận dụng CloudWatch và Performance Insights để "bắt mạch" hệ thống.
-   **Tối ưu chi phí:** Các bí quyết quản lý tài nguyên để đạt hiệu suất cao nhất với chi phí hợp lý nhất.
