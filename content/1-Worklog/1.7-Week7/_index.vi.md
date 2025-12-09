---
title: "Worklog tuần 7"
date: 2024-10-21
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7

-   **Tổng hợp kiến thức chiến lược:** Thực hiện rà soát và hệ thống hóa toàn diện các năng lực AWS cốt lõi để chuẩn bị cho kỳ đánh giá giữa kỳ.
-   **Mô phỏng kỳ thi:** Tham gia thực hành nghiêm ngặt các bài lab và bộ câu hỏi tình huống trên nền tảng **AWS Builders** và **AWSboy** để làm quen với định dạng đề thi.
-   **Hệ thống hóa kiến trúc:** Rà soát có cấu trúc về mối tương quan giữa các dịch vụ nền tảng: EC2, S3, VPC, IAM, RDS, Lambda và DynamoDB.

---

### Nhiệm vụ thực hiện trong tuần

| Ngày    | Hoạt động                                                                                                                                                                                                                                                                                                                    | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo   |
| :------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------- | :-------------- | :------------------- |
| Thứ Hai | - **Tổng hợp kiến trúc tính toán:** Nghiên cứu sâu về vòng đời EC2 và mô hình hướng sự kiện của Lambda. <br> - **Thực hành mô phỏng:** Thực hiện quản lý trọn vẹn vòng đời **EC2 Instances** (Từ khởi tạo đến hủy bỏ). <br> - **Serverless Review:** Phân tích môi trường thực thi và logic kích hoạt (triggers) của Lambda. | 22/10/2024   | 22/10/2024      | AWS Builders, AWSboy |
| Thứ Ba  | - **Phân tích phân cấp lưu trữ:** So sánh các mô hình lưu trữ Block (EBS), Object (S3), và File (EFS). <br> - **Triển khai thực tế:** Cấu hình chiến lược phân tầng S3 (Standard, IA, Glacier) và các loại EBS volume. <br> - **Kiểm soát bảo mật:** Thực thi các chính sách bucket S3 và ACL chi tiết.                      | 23/10/2024   | 23/10/2024      | AWS Builders, AWSboy |
| Thứ Tư  | - **Kỹ thuật tô-pô mạng:** Phẫu thuật cấu trúc VPC (Subnetting, Route Tables, IGW, các lớp bảo mật). <br> - **Kiểm thử tình huống:** Phân biệt cấu hình giữa Security Group (Stateful) và NACL (Stateless). <br> - **Kết nối:** Rà soát giao tiếp liên mạng thông qua VPC Peering và Transit Gateway.                        | 24/10/2024   | 24/10/2024      | AWS Builders, AWSboy |
| Thứ Năm | - **Lưu trữ & Quản trị:** Củng cố kiến thức về mô hình dữ liệu (RDS vs. DynamoDB) và Quản trị định danh (IAM). <br> - **Quản lý danh tính:** Kiến trúc các **IAM Policies**, **Roles**, và phân cấp **User** an toàn. <br> - **Cấu hình Database:** Thực hành lập kế hoạch dung lượng DynamoDB và cấp phát RDS instance.     | 25/10/2024   | 25/10/2024      | AWS Builders, AWSboy |
| Thứ Sáu | - **Đánh giá độ sẵn sàng:** Thực hiện các **bài thi thử tổng hợp** trên các nền tảng mô phỏng. <br> - **Phân tích lỗ hổng:** Xác định và khắc phục các vùng kiến thức yếu bộc lộ trong quá trình kiểm tra. <br> - **Tài sản tri thức:** Tổng hợp ghi chú tóm tắt (cheat sheets) để tra cứu nhanh trước giờ thi.              | 26/10/2024   | 26/10/2024      | AWS Builders, AWSboy |

---

### Kết quả đạt được trong tuần 7

**Năng lực toàn diện đạt được:**

-   **Làm chủ dịch vụ:** Đạt được sự hiểu biết toàn diện về các trụ cột trong Khung Chuyển đổi Đám mây AWS: Compute, Storage, Networking, Database, và Security.
-   **Thành thạo xử lý tình huống:** Vượt qua thành công các bài lab phức tạp và các câu hỏi trắc nghiệm hóc búa trên **AWS Builders** và **AWSboy**.
-   **Thông thạo vận hành:**
    -   **Compute:** Nắm vững các tham số EC2 (Các họ Instance, lựa chọn AMI, tối ưu hóa EBS).
    -   **Storage:** Thấu hiểu quản lý đối tượng S3 và bài toán kinh tế trong vòng đời dữ liệu.
-   **Chiều sâu về mạng:** Đạt được sự rõ ràng về các thành phần kiến trúc **VPC** (Cô lập Public/Private, Logic định tuyến, Bảo mật phòng thủ theo chiều sâu).
-   **Sẵn sàng cho kỳ thi:** Đạt mức độ tự tin cao thông qua quá trình kiểm tra và ôn tập lặp lại.
-   **Cơ sở tri thức:** Xây dựng kho lưu trữ ghi chú học tập tập trung bao phủ tất cả các nhóm dịch vụ chính.
-   **Khắc phục:** Chủ động giải quyết và lấp đầy các lỗ hổng kiến thức được phát hiện trong các phiên thực hành.

**Đúc kết cốt lõi:**

-   **Phân lớp bảo mật:** Security Group hoạt động như tường lửa có trạng thái (tự động cho phép lưu lượng phản hồi), trong khi NACL là không trạng thái (yêu cầu quy tắc hai chiều rõ ràng).
-   **Tối ưu hóa Workload:** Các họ EC2 instance được thiết kế chuyên biệt cho các điểm nghẽn cụ thể (Tính toán, Bộ nhớ, Lưu trữ, hoặc GPU).
-   **Bài toán kinh tế lưu trữ:** Các lớp lưu trữ S3 được thiết kế để cân bằng giữa chi phí truy xuất và yêu cầu về tần suất truy cập.
-   **Logic IAM:** Việc đánh giá Policy tuân theo nguyên tắc mặc định "Implicit Deny", trong đó chính sách hạn chế nhất (Explicit Deny) luôn chiến thắng.
-   **Độ chính xác định tuyến:** Các quyết định định tuyến trong VPC dựa trên nguyên tắc "Longest Prefix Match" (Khớp tiền tố dài nhất) để xác định đường đi của lưu lượng.
