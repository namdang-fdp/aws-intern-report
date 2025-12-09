---
title: "Worklog tuần 3"
date: 2025-09-21
weight: 3
chapter: false
pre: "<b>1.3. </b>"
---

### Mục tiêu tuần 3

-   Khắc phục các vấn đề về tài khoản AWS và khởi tạo tài khoản mới nếu cần thiết.
-   Thành thạo kiến trúc Hybrid DNS sử dụng Route 53 Resolver.
-   Thiết lập và nắm vững kết nối mạng riêng tư thông qua VPC Peering.
-   Hoạch định lộ trình dự án và thống nhất ngôn ngữ lập trình phát triển.

### Nhiệm vụ thực hiện trong tuần

| Ngày | Hoạt động                                                                                                                                                                                                                                                                                                                                               | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                                                                   |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ------------------------------------------------------------------------------------ |
| 2    | - **Quản trị định danh:** Triển khai kiểm soát truy cập và phân quyền sử dụng AWS Identity and Access Management (IAM).                                                                                                                                                                                                                                 | 21/09/2025   | 23/09/2025      | [AWS IAM Access Control](https://000002.awsstudygroup.com/)                          |
| 3    | - **Thực hành Lab:** Thực hiện Lab 10 tập trung vào thiết lập Hybrid DNS và Route 53.<br>- **Triển khai:** Khởi tạo các EC2 instance để kiểm chứng logic phân giải DNS.<br>- **Hoàn thành:** Kết thúc học phần _Hybrid DNS Management with Amazon Route 53_.                                                                                            | 24/09/2025   | 25/09/2025      | [FCJ Playlist](https://youtube.com/playlist?list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i) |
| 4    | - **Tích hợp mạng:** Cấu hình VPC Peering để điều hướng lưu lượng riêng tư giữa các VPC khác nhau.<br>- **Cấp phát tài nguyên:** Triển khai các tài nguyên cần thiết để hỗ trợ mô hình peering.<br>- **Dọn dẹp:** Hủy bỏ tài nguyên sau khi thực hành để tối ưu chi phí.<br>- **Hoàn thành:** Kết thúc học phần _Network Integration with VPC Peering_. | 25/09/2025   | 26/09/2025      | [AWS VPC Peering](https://docs.aws.amazon.com/vpc/latest/peering/)                   |
| 5    | - **Lập kế hoạch chiến lược:** Tham gia họp nhóm để chốt phương án công nghệ (tech stack) và định hướng dự án.<br>- **Lên lịch trình:** Xác định các cột mốc để thành viên nghiên cứu công nghệ đã chọn.                                                                                                                                                | 28/09/2025   | 28/09/2025      | Team Meeting                                                                         |

### Các khóa học AWS Skill Builder đã hoàn thành

| Khóa học                                       | Danh mục    | Trạng thái |
| ---------------------------------------------- | ----------- | ---------- |
| Hybrid DNS Management with Amazon Route 53     | Networking  | ✅         |
| Network Integration with VPC Peering           | Networking  | ✅         |
| Networking on AWS Workshop                     | Networking  | ✅         |
| Infrastructure as Code with AWS CloudFormation | DevOps      | ✅         |
| Cloud Development with AWS Cloud9              | Development | ✅         |
| Static Website Hosting with Amazon S3          | Storage     | ✅         |

### Kết quả đạt được trong tuần 3

**Năng lực kỹ thuật:**

_Kiến trúc Route 53 & Hybrid DNS:_

-   Xây dựng thành công hệ sinh thái Hybrid DNS vững chắc tận dụng Route 53 Resolver.

-   Cấp phát **Outbound Endpoints** để chuyển tiếp các truy vấn DNS từ AWS về môi trường on-premises.
-   Định nghĩa các **Resolver Rules** chi tiết để quản lý logic chuyển tiếp có điều kiện.
-   Thiết lập **Inbound Endpoints** cho phép mạng nội bộ (on-premises) phân giải các domain được host trên AWS.
-   Kiểm chứng kết nối thành công thông qua RD Gateway Server trong quá trình thực hành.

_VPC Peering & Kết nối liên mạng:_

-   Nắm vững cơ chế vận hành của VPC Peering để đảm bảo giao tiếp riêng tư an toàn mà không lộ ra public internet.

-   Kích hoạt và kiểm thử **Phân giải DNS xuyên Zone và Region** trong VPC Peering:
    -   Cho phép các EC2 instance phân giải hostname của đối tác sang địa chỉ Private IP.
    -   Nhận thức rõ việc thiếu cấu hình này sẽ buộc phân giải sang Public IP, khiến lưu lượng đi vòng qua internet một cách không cần thiết.
-   Thực hành nghiêm ngặt quy trình hủy tài nguyên để ngăn chặn phát sinh chi phí.

_Cơ sở hạ tầng dưới dạng mã (IaC) & Công cụ phát triển:_

-   Có khả năng triển khai cơ sở hạ tầng AWS sử dụng các template **CloudFormation**.
-   Nắm bắt mô hình quản lý hạ tầng theo hướng khai báo (declarative).
-   Tìm hiểu **AWS Cloud9** như một môi trường phát triển tích hợp (IDE) trên trình duyệt.

**Tiến độ hợp tác nhóm:**

-   Đóng góp vào các buổi hoạch định cấp cao để xác định hướng đi phát triển dự án.
-   Đạt được sự đồng thuận tuyệt đối về ngôn ngữ lập trình cho dự án sắp tới.
-   Thiết lập lộ trình học tập rõ ràng để cả nhóm làm chủ công nghệ đã chọn.
-   Duy trì sự tương tác và hỗ trợ tích cực trong đội ngũ FCJ.

**Đúc kết cốt lõi:**

-   **Hybrid DNS** đóng vai trò cầu nối quan trọng cho việc phân giải tên miền liền mạch giữa hệ thống on-prem cũ và môi trường cloud hiện đại.
-   **VPC Peering** cung cấp giải pháp kết nối mạng tối ưu chi phí, tuy nhiên cần lưu ý các hạn chế như không hỗ trợ bắc cầu (transitive peering).
-   **CloudFormation** đảm bảo tính nhất quán và khả năng tái lập của hạ tầng thông qua mã nguồn.
-   **AWS Cloud9** giảm thiểu đáng kể sự phức tạp khi thiết lập môi trường phát triển cục bộ (local).
