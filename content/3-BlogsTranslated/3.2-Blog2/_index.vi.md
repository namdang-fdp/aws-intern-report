---
title: "Ngăn chặn việc mã hóa ngoài ý muốn đối với các đối tượng trong Amazon S3"
date: 2025-01-15
weight: 3
chapter: false
pre: " <b> 3.2. </b> "
---

Ngày đăng: 15-01-2025 – Tác giả: Steve de Vera, Jennifer Paz trong [Amazon S3](https://aws.amazon.com/blogs/storage/category/storage/amazon-s3/), [Security, Identity, & Compliance](https://aws.amazon.com/blogs/security/), [Best Practices](https://aws.amazon.com/blogs/architecture/category/best-practices/).

-   **Cập nhật ngày 18 tháng 3 năm 2025:** Bài viết này đã được cập nhật để bổ sung thêm hướng dẫn về việc giám sát và phát hiện.
-   **Cập nhật ngày 17 tháng 1 năm 2025:** Chúng tôi đã cập nhật bài viết này để nhấn mạnh tầm quan trọng của việc sử dụng thông tin xác thực ngắn hạn nhằm giảm thiểu rủi ro từ các kỹ thuật truy cập trái phép tương tự như kỹ thuật được mô tả trong bài viết này.

Tại Amazon Web Services (AWS), bảo mật cho dữ liệu của khách hàng luôn là ưu tiên hàng đầu — và sẽ luôn như vậy. Gần đây, Nhóm Ứng phó sự cố khách hàng của AWS (AWS Customer Incident Response Team – CIRT) cùng với các hệ thống giám sát bảo mật tự động của chúng tôi đã phát hiện sự gia tăng bất thường trong hoạt động mã hóa liên quan đến các bucket của Amazon Simple Storage Service (Amazon S3).

Điều quan trọng cần lưu ý là các hành động này **không khai thác lỗ hổng trong bất kỳ dịch vụ nào của AWS** — mà yêu cầu thông tin xác thực hợp lệ bị người dùng trái phép sử dụng theo cách ngoài ý muốn. Mặc dù các hành động này diễn ra trong phạm vi trách nhiệm của khách hàng theo mô hình trách nhiệm chia sẻ (shared responsibility model), AWS vẫn khuyến nghị một số bước mà khách hàng có thể thực hiện để ngăn chặn hoặc giảm thiểu tác động của loại hoạt động này.

Khi phối hợp cùng khách hàng, các nhóm bảo mật của chúng tôi đã phát hiện sự gia tăng các sự kiện mã hóa dữ liệu trong S3 bằng phương thức **mã hóa phía máy chủ với khóa do khách hàng cung cấp (SSE-C)**. Mặc dù đây là một tính năng được nhiều khách hàng sử dụng, chúng tôi đã phát hiện một mô hình trong đó một lượng lớn các thao tác `S3 CopyObject` sử dụng SSE-C bắt đầu ghi đè lên các đối tượng, dẫn đến việc mã hóa lại dữ liệu khách hàng bằng khóa mã hóa mới. Phân tích của chúng tôi cho thấy điều này được thực hiện bởi các tác nhân độc hại đã có được thông tin xác thực hợp lệ của khách hàng và dùng chúng để mã hóa lại các đối tượng.

Bằng cách sử dụng các công cụ phòng thủ chủ động (active defense tools), chúng tôi đã triển khai các biện pháp giảm thiểu tự động (automatic mitigations) giúp ngăn chặn loại hoạt động trái phép này trong nhiều trường hợp. Tuy nhiên, do các tác nhân đe dọa sử dụng thông tin xác thực hợp lệ, nên rất khó để AWS có thể phân biệt một cách chắc chắn giữa việc sử dụng hợp pháp và sử dụng độc hại. Vì vậy, chúng tôi khuyến nghị khách hàng tuân thủ các thực hành bảo mật tốt nhất để giảm thiểu rủi ro.

Chúng tôi khuyến nghị khách hàng triển khai bốn thực hành bảo mật chính sau để bảo vệ khỏi việc sử dụng SSE-C trái phép:

1.  Triển khai thông tin xác thực ngắn hạn.
2.  Triển khai quy trình khôi phục dữ liệu.
3.  Giám sát tài nguyên AWS để phát hiện các mẫu truy cập bất thường.
4.  Chặn việc sử dụng SSE-C, trừ khi ứng dụng của bạn thực sự yêu cầu.

---

### 1. Triển khai thông tin xác thực ngắn hạn

Mặc dù kỹ thuật trên có sử dụng phương thức mã hóa SSE-C, nhưng nguyên nhân gốc rễ của vấn đề này — cũng như phần lớn các sự cố bảo mật — xuất phát từ việc bị lộ hoặc xâm phạm khóa truy cập dài hạn. Cách hiệu quả nhất để giảm thiểu rủi ro từ các thông tin xác thực bị xâm phạm là không tạo ra thông tin xác thực dài hạn ngay từ đầu.

-   **IAM Roles**: Cho phép các ứng dụng gửi yêu cầu API có ký xác thực một cách an toàn từ Amazon EC2, Amazon ECS, Amazon EKS hoặc Lambda bằng cách sử dụng thông tin xác thực ngắn hạn.
-   **IAM Roles Anywhere**: Cho phép các hệ thống bên ngoài môi trường AWS Cloud thực hiện các cuộc gọi đã xác thực mà không cần dùng thông tin xác thực dài hạn.
-   **AWS IAM Identity Center**: Cho phép các máy trạm của nhà phát triển lấy thông tin xác thực ngắn hạn được bảo vệ bởi danh tính người dùng dài hạn — vốn được tăng cường bảo mật bằng xác thực đa yếu tố (MFA).

Những công nghệ này dựa trên **AWS Security Token Service (AWS STS)** để cấp phát thông tin xác thực bảo mật tạm thời.

---

### 2. Triển khai quy trình khôi phục dữ liệu

Nếu không có các cơ chế bảo vệ dữ liệu được thiết lập, thời gian khôi phục dữ liệu có thể sẽ kéo dài hơn. Chúng tôi khuyến nghị bạn nên bảo vệ dữ liệu khỏi việc bị ghi đè và duy trì một bản sao thứ hai của các dữ liệu quan trọng.

-   **S3 Versioning**: Bật tính năng này để lưu nhiều phiên bản của một đối tượng trong bucket, giúp khôi phục lại các đối tượng bị xóa hoặc ghi đè ngoài ý muốn. Sử dụng **S3 Lifecycle** để quản lý các phiên bản cũ và kiểm soát chi phí.
-   **S3 Replication**: Sao chép dữ liệu quan trọng sang một bucket khác (có thể khác tài khoản hoặc khác vùng AWS). Dịch vụ này cung cấp SLA cho các yêu cầu nghiêm ngặt về RPO và RTO.
-   **AWS Backup cho S3**: Dịch vụ được quản lý giúp tự động hóa việc sao lưu định kỳ cho các bucket S3.

---

### 3. Giám sát tài nguyên AWS để phát hiện các mẫu truy cập bất thường

Nếu không có cơ chế giám sát, các hành động trái phép trên các bucket S3 có thể không được phát hiện.

-   **AWS CloudTrail**: Ghi lại các sự kiện trên nhiều dịch vụ AWS. Bạn có thể kiểm tra log CloudTrail để tìm giá trị `requestParameters.x-amz-server-side-encryption-customer-algorithm` trong các sự kiện dữ liệu S3 để xác định xem SSE-C có đang được sử dụng hay không.
-   **Amazon CloudWatch**: Tạo các cảnh báo (alarms) dựa trên các chỉ số hoặc log cụ thể.
-   **Amazon EventBridge & AWS Lambda**: Thiết lập tự động hóa để thực hiện các biện pháp khắc phục.
-   **Amazon GuardDuty**: Cấu hình GuardDuty và bật **S3 Protection** với **Extended Threat Detection**. Cách này giúp GuardDuty phát hiện các hoạt động rò rỉ dữ liệu tiềm ẩn hoặc các nỗ lực tấn công ransomware thông qua mã hóa SSE-C.

---

### 4. Chặn việc sử dụng mã hóa SSE-C

Nếu ứng dụng của bạn không sử dụng SSE-C làm phương thức mã hóa, bạn có thể chặn việc sử dụng SSE-C bằng cách áp dụng chính sách tài nguyên cho bucket S3 hoặc chính sách kiểm soát tài nguyên (RCP) trong AWS Organizations.

**S3 Bucket Policy**

Ví dụ dưới đây minh họa một bucket policy chặn yêu cầu SSE-C cho bucket có tên `<your-bucket-name>`:

```json
{
    "Version": "2012-10-17",
    "Id": "S3-Console-Auto-Gen-Policy",
    "Statement": [
        {
            "Sid": "DenySSE-C",
            "Effect": "Deny",
            "Principal": "*",
            "Action": "s3:PutObject",
            "Resource": "arn:aws:s3:::<your-bucket-name>/*",
            "Condition": {
                "Null": {
                    "s3:x-amz-server-side-encryption-customer-algorithm": "false"
                }
            }
        }
    ]
}
```

AWS Organizations Resource Control Policy (RCP)

RCP cho phép khách hàng xác định giới hạn quyền truy cập tối đa áp dụng cho các tài nguyên trên toàn bộ tổ chức. Ví dụ sau minh họa một RCP chặn các yêu cầu SSE-C đối với tất cả bucket trong tổ chức:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "DenySSE-C",
            "Effect": "Deny",
            "Principal": "*",
            "Action": "s3:PutObject",
            "Resource": "*",
            "Condition": {
                "Null": {
                    "s3:x-amz-server-side-encryption-customer-algorithm": "false"
                }
            }
        }
    ]
}
```

Tổng kết

Điều quan trọng và có giá trị nhất bạn có thể làm để bảo vệ môi trường AWS của mình khỏi các mối đe dọa phổ biến là loại bỏ hoặc giảm thiểu việc sử dụng thông tin xác thực dài hạn. Trong khi đội ngũ bảo mật của bạn không ngừng bảo vệ hệ thống, các nhóm của AWS — bao gồm AWS CIRT, Amazon Threat Intelligence và Amazon S3 team — đang liên tục đổi mới để bảo vệ dữ liệu quý giá của bạn.

Nếu bạn nghi ngờ có hoạt động trái phép, hãy liên hệ ngay lập tức với AWS Support để được hỗ trợ.
