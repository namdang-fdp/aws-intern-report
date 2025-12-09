---
title: "Hướng dẫn dành cho Nhà phát triển Game về Amazon DocumentDB (tương thích với MongoDB)"
date: 2024-01-25
weight: 4
chapter: false
pre: " <b> 3.3. </b> "
---

Ngày đăng: 25-01-2024 – Tác giả: Jackie Jiang, Douglas Bonser, Matthew Nimmo trong [Game Tech](https://aws.amazon.com/blogs/gametech/), [Databases](https://aws.amazon.com/blogs/database/), [Amazon DocumentDB](https://aws.amazon.com/blogs/database/category/database/amazon-documentdb/).

---

**Giới thiệu**

Tiếp nối cuộc thảo luận về các phương pháp thực hành tốt nhất của Amazon DocumentDB trong phần hai, bài viết này sẽ tập trung vào bảo vệ dữ liệu, khả năng mở rộng, giám sát và tối ưu hóa chi phí.

---

**Bảo vệ dữ liệu**

Để bảo vệ dữ liệu được lưu trữ trong Amazon DocumentDB, bạn nên mã hóa dữ liệu bằng cách bật tùy chọn storage encryption khi tạo cụm (cluster). Việc mã hóa được bật mặc định trên toàn cụm và áp dụng cho tất cả các instance, log, bản sao lưu tự động và snapshot. Amazon DocumentDB xử lý việc mã hóa và giải mã dữ liệu một cách trong suốt, với tác động tối thiểu đến hiệu năng. Bạn có thể sử dụng khóa mặc định của AWS hoặc tự cung cấp khóa riêng để mã hóa dữ liệu của mình.

Amazon DocumentDB hỗ trợ kiểm soát truy cập dựa trên vai trò (RBAC), nên được sử dụng để giới hạn quyền truy cập chỉ đọc đối với các cơ sở dữ liệu hoặc tập hợp, cũng như trong các thiết kế ứng dụng đa người dùng. Bài viết [Introducing role-based access control for Amazon DocumentDB (with MongoDB compatibility)](https://aws.amazon.com/blogs/database/introducing-role-based-access-control-for-amazon-documentdb-with-mongodb-compatibility/) giải thích chi tiết các khái niệm và khả năng của RBAC trong Amazon DocumentDB.

Bằng cách sử dụng **AWS Secrets Manager**, bạn có thể lấy mật khẩu Amazon DocumentDB một cách lập trình và tự động xoay vòng (rotate) chúng, thay thế cho việc hardcode thông tin xác thực trong mã nguồn, như đã mô tả trong bài [How to rotate Amazon DocumentDB and Amazon Redshift credentials in AWS Secrets Manager](https://aws.amazon.com/blogs/security/how-to-rotate-amazon-documentdb-and-amazon-redshift-credentials-in-aws-secrets-manager/).

**AWS CloudTrail** tích hợp với Amazon DocumentDB, cung cấp bản ghi theo dõi các hành động cơ sở dữ liệu được thực hiện bởi người dùng, vai trò hoặc các dịch vụ AWS khác, đồng thời ghi lại mọi lệnh gọi API cho Amazon DocumentDB. Xem thêm [Logging Amazon DocumentDB API Calls with AWS CloudTrail](https://docs.aws.amazon.com/documentdb/latest/developerguide/logging-using-cloudtrail.html) để biết chi tiết.

Ngoài ra, bạn có thể bật tính năng auditing của Amazon DocumentDB để ghi lại các sự kiện DDL, DML, xác thực, phân quyền, và quản lý người dùng vào Amazon CloudWatch Logs ở định dạng tài liệu JSON. Xem thêm về [Auditing Amazon DocumentDB Events](https://docs.aws.amazon.com/documentdb/latest/developerguide/auditing.html) để biết thêm chi tiết.

---

**Mở rộng quy mô**

Như đã đề cập trong phần một, Amazon DocumentDB hỗ trợ cả mở rộng theo chiều dọc và mở rộng theo chiều ngang. Trong phần này, chúng ta sẽ đi sâu hơn vào các chủ đề: tính nhất quán của dữ liệu đọc, ưu tiên đọc, lưu lượng đọc và ghi, ưu tiên đọc động, và tải công việc bất đối xứng.

Hãy cùng tìm hiểu về **tính nhất quán khi đọc** và **ưu tiên đọc**. Các thao tác đọc từ instance chính có tính nhất quán mạnh, đảm bảo khả năng đọc sau khi ghi. Ở phía ngược lại, khi đọc từ các bản sao, dữ liệu chỉ đạt được tính nhất quán dần theo thời gian. Độ trễ giữa primary và replica thường nhỏ hơn 100ms. Để mở rộng khả năng đọc, bạn nên sử dụng các replica instance. Việc này được thực hiện bằng cách đặt `readPreference` là `secondaryPreferred`. Trong trường hợp một replica bị lỗi, yêu cầu đọc sẽ được chuyển hướng đến replica khả dụng tiếp theo. Cuối cùng, nếu không có replica nào khả dụng, các thao tác đọc sẽ được chuyển về primary instance.

Bây giờ khi chúng ta đã hiểu tổng quan về cách hoạt động của tính nhất quán và ưu tiên khi đọc, hãy nói về việc **mở rộng lưu lượng đọc**. Giả sử bạn có một cụm gồm ba instance (một primary và hai read replica) và bạn muốn mở rộng để hỗ trợ lưu lượng đọc cao. Bạn chỉ cần thêm các read replica! Bạn có thể mở rộng tối đa lên đến 15 read replica cho mỗi cụm. Nếu bạn sử dụng `readPreference` là `secondaryPreferred`, driver sẽ tự động sử dụng các replica mới. Đôi khi bạn có thể muốn giữ thiết lập mặc định của mình, nhưng cần ghi đè trên từng truy vấn để đạt tính nhất quán cao hơn. Ví dụ, trong khi mặc định của bạn đang trỏ tới read replica `secondaryPreferred`, bạn có thể tạo một truy vấn ghi đè để lấy dữ liệu trực tiếp từ "primary".

Mặc dù thông thường được khuyến nghị sử dụng các instance đồng nhất trong một cụm, bạn vẫn có thể cân nhắc đến các **tải công việc bất đối xứng**. Ví dụ, nếu tải công việc của bạn có nhu cầu phân tích đột xuất hoặc định kỳ như chạy báo cáo hàng tháng, bạn có thể tối ưu kích thước cụm cho khối lượng công việc trực tuyến và thêm một node mới dành riêng cho phân tích. Từ đó, bạn chạy các truy vấn báo cáo trên node mới này, và khi hoàn tất, bạn có thể tắt node đó để tiết kiệm chi phí.

Đến đây, chúng ta đã nói về nhu cầu mở rộng cho việc đọc, nhưng hãy tập trung vào chiến lược **mở rộng cho việc ghi**! Giả sử lưu lượng ghi của bạn tăng lên hoặc bạn dự đoán nó sẽ tăng. Hiện tại bạn đang sử dụng cụm gồm ba instance loại `r6g.large`, nhưng muốn chuyển sang `r6g.4xlarge`. Đầu tiên, bạn sẽ thêm ba node `r6g.4xlarge` mới vào cụm, và để đảm bảo an toàn, bạn sẽ chọn mức promotion tier cao hơn cho các node có kích thước lớn hơn. Lưu ý rằng Amazon DocumentDB mặc định sẽ ưu tiên chọn các node lớn hơn làm primary. Bây giờ đến phần quan trọng — bạn kích hoạt auto failover và instance lớn hơn sẽ tự động được chọn làm primary. Khi điều đó xảy ra, bạn có thể xóa các instance `r6g.large` nhỏ hơn một cách an toàn. Hình dưới đây mô phỏng quy trình này.

![Mở rộng quy mô ghi](/images/3-BlogsTranslated/Blog4/img1.jpg)

Cuối cùng, hãy kết thúc chủ đề mở rộng bằng việc nói về **lưu trữ và I/O**. Cả lưu trữ (storage) và I/O đều được tự động mở rộng trong Amazon DocumentDB. Lưu trữ được mở rộng theo từng phân đoạn 10GiB, với dung lượng tối đa 128TiB. Nếu bạn đang di chuyển khối lượng công việc sang Amazon DocumentDB và dự định xóa một số dữ liệu, chẳng hạn dữ liệu lịch sử không còn cần thiết, hãy thực hiện việc đó trước khi di chuyển dữ liệu sang Amazon DocumentDB để giảm chi phí.

---

**Giám sát**

Chủ đề giám sát trong nhiều dịch vụ AWS rất phong phú về chi tiết và tính năng, và Amazon DocumentDB cũng không ngoại lệ. Hãy cùng xem tổng quan các lĩnh vực chính bao quát khả năng giám sát của dịch vụ này.

**Amazon CloudWatch**

Amazon DocumentDB công bố hơn 50 chỉ số vận hành (operational metrics) lên CloudWatch có thể được theo dõi. CloudWatch cho phép bạn đặt cảnh báo (alarms) và gửi thông báo khi các chỉ số vượt quá giá trị định sẵn. Các chỉ số này cung cấp thông tin về:

-   **Instance**: `BufferCacheHitRatio`, `FreeableMemory`, v.v.
-   **Cluster**: `DBClusterReplicaLagMaximum`, `VolumeWriteIOPS`, v.v.
-   **Lưu trữ**: `VolumeBytesUsed`.
-   **Sao lưu**: `SnapshotStorageUsed`, `TotalBackupStorageBilled`, v.v.

Nếu bạn muốn tìm hiểu sâu hơn về các chỉ số CloudWatch của Amazon DocumentDB, hãy xem bài viết [Monitoring metrics and setting up alarms on your Amazon DocumentDB clusters](https://aws.amazon.com/blogs/database/monitoring-metrics-and-setting-up-alarms-on-your-amazon-documentdb-clusters/) để biết chi tiết.

**Profiler và Auditing**

-   **Profiler là gì?** Profiler giúp bạn xác định các truy vấn chậm và khám phá cơ hội để tạo các chỉ mục (index) mới. Ngoài ra, nó còn giúp phát hiện những tối ưu hóa cần thiết cho các chỉ mục hiện có nhằm cải thiện hiệu năng truy vấn. Bạn đặt một ngưỡng (threshold), và bất kỳ thao tác nào chạy lâu hơn ngưỡng đó sẽ được ghi lại vào CloudWatch Logs. Bạn có thể sử dụng các log này để xác định truy vấn nào không sử dụng chỉ mục hoặc sử dụng chỉ mục chưa tối ưu. Cuối cùng, việc bật profiler sẽ giúp bạn khắc phục các truy vấn chạy chậm. Xem chi tiết tại [Profiling Amazon DocumentDB Operations](https://docs.aws.amazon.com/documentdb/latest/developerguide/profiling.html).

-   **Auditing là gì?** Auditing cho phép bạn ghi lại một số sự kiện nhất định xảy ra trong Amazon DocumentDB. Các sự kiện này có thể bao gồm sự kiện DDL (phân quyền, quản lý người dùng, tạo chỉ mục, v.v.) và DML (tạo, đọc, cập nhật, xóa). Vì log kiểm toán được ghi vào CloudWatch Logs, bạn có thể đặt cảnh báo (alarm) cho các hoạt động cụ thể. Ví dụ: 10 lần đăng nhập sai trong vòng một phút. Xem chi tiết tại [Introducing DML auditing for Amazon DocumentDB](https://aws.amazon.com/blogs/database/introducing-dml-auditing-for-amazon-documentdb-with-mongodb-compatibility/).

Profiler và auditing bị tắt theo mặc định, nên bạn cần kích hoạt và cấu hình chúng trước khi sử dụng. Bạn có thể tham khảo hướng dẫn dành cho nhà phát triển qua các liên kết:

-   [Cách bật profiler?](https://docs.aws.amazon.com/documentdb/latest/developerguide/profiling.html#profiling-enabling)
-   [Cách kích hoạt auditing?](https://docs.aws.amazon.com/documentdb/latest/developerguide/auditing.html#auditing-enabling)

**Chi tiết về hiệu suất (Performance Insights)**

Performance Insights mở rộng các tính năng giám sát sẵn có của Amazon DocumentDB để giúp bạn minh họa hiệu năng cụm (cluster) và phân tích các vấn đề ảnh hưởng đến nó. Với bảng điều khiển Performance Insights, bạn có thể trực quan hóa tải của cơ sở dữ liệu, lọc tải theo loại đợi (waits), câu lệnh truy vấn, máy chủ (hosts), hoặc ứng dụng. Performance Insights được tích hợp sẵn với các instance của Amazon DocumentDB và lưu giữ lịch sử hiệu năng 7 ngày gần nhất mà không tính thêm chi phí. Tính năng này bị tắt theo mặc định và có thể được bật theo từng instance. Để xem minh họa nhanh, hãy xem video [Getting started with Amazon DocumentDB Observability and Monitoring](https://www.youtube.com/watch?v=EXAMPLE).

**Đăng ký sự kiện**

Cuối cùng, bạn có thể đăng ký (subscribe) các sự kiện xảy ra trong Amazon DocumentDB. Dịch vụ này phân loại các sự kiện thành nhiều nhóm để bạn có thể đăng ký nhận thông báo khi sự kiện trong nhóm đó xảy ra. Các loại sự kiện bao gồm: cluster, instance, cluster snapshot, và parameter group. Bạn có thể dễ dàng đăng ký tất cả sự kiện trong một nhóm (ví dụ: tất cả sự kiện của cluster) hoặc chỉ một sự kiện cụ thể từ một tài nguyên nhất định (ví dụ: sự kiện failover của primary instance trong cụm sản xuất). Các sự kiện này được tạo mặc định, không cần cấu hình thêm trong Amazon DocumentDB. Xem chi tiết tại [Using Amazon DocumentDB Event Subscriptions](https://docs.aws.amazon.com/documentdb/latest/developerguide/event-subscriptions.html).

---

**Tối ưu hóa chi phí**

Amazon DocumentDB tính phí theo giây sử dụng, với thời gian tính tối thiểu là 10 phút. Để chủ động quản lý chi tiêu cho các cụm DocumentDB, bạn nên tạo cảnh báo hóa đơn ở các ngưỡng 50% và 75% của chi phí dự kiến trong tháng. Xem hướng dẫn [Create a billing alarm](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitor_estimated_charges_with_cloudwatch.html) để biết cách tạo cảnh báo hóa đơn. Bạn cũng có thể theo dõi chi phí chi tiết bằng cách gắn tag cho cụm và instance. Để hiểu cách theo dõi chi phí instance, lưu trữ, IOPS và sao lưu, hãy đọc [Using cost allocation tags with Amazon DocumentDB](https://docs.aws.amazon.com/documentdb/latest/developerguide/tagging.html).

Đối với môi trường không phải sản xuất, bạn nên tạm dừng tất cả instance trong cụm (tối đa 7 ngày) khi không cần thiết, và khởi động lại khi cần làm việc. Khi cụm bị dừng, bạn chỉ bị tính phí lưu trữ, snapshot thủ công, và backup tự động trong thời gian lưu giữ đã cấu hình. Bạn không bị tính phí giờ chạy instance. Xem chi tiết tại [Stopping and Starting an Amazon DocumentDB Cluster](https://docs.aws.amazon.com/documentdb/latest/developerguide/db-cluster-stop-start.html).

Thiết kế của Amazon DocumentDB tách biệt tính toán và lưu trữ. Dữ liệu được nhân bản 6 lần trên 3 vùng khả dụng, đảm bảo độ bền dữ liệu cao bất kể số lượng instance trong cụm. Khuyến nghị sử dụng tối thiểu 3 instance cho môi trường sản xuất để đảm bảo tính sẵn sàng cao; trong khi với môi trường thử nghiệm, bạn có thể chỉ cần 1 instance nếu chấp nhận được thời gian downtime.

Cả **Time To Live indexes** và **change streams** sẽ tạo thêm các thao tác I/O khi dữ liệu được đọc, chèn, cập nhật hoặc xóa. Nếu ứng dụng của bạn không sử dụng các tính năng này, hãy tắt chúng để giảm chi phí.

Khi dữ liệu của bạn tăng lên, hãy xem xét triển khai chiến lược lưu trữ dữ liệu lâu dài phù hợp để chỉ giữ dữ liệu đang hoạt động trong cụm, còn dữ liệu truy cập ít có thể lưu sang các lựa chọn lưu trữ chi phí thấp hơn như Amazon S3. Xem hướng dẫn [Optimize data archival costs in Amazon DocumentDB using rolling collections](https://aws.amazon.com/blogs/database/optimize-data-archival-costs-in-amazon-documentdb-using-rolling-collections/) để hiểu cách triển khai chiến lược lưu trữ này.

Khi tối ưu chi phí, đừng quên yếu tố sao lưu (backups). Bạn không thể tắt backup, với thời gian lưu giữ tối thiểu 1 ngày và tối đa 35 ngày. Như các thông lệ tốt khác về khả năng phục hồi dữ liệu, hãy đặt thời gian lưu giữ dựa trên RPO (Recovery Point Objective) của bạn. Cửa sổ backup (backup window) bạn định nghĩa cũng có thể dùng để tự động tạo môi trường phát triển hoặc kiểm thử từ snapshot. Cuối cùng, việc sao lưu dữ liệu có thể mất đến 5 phút để cập nhật dữ liệu mới nhất, nghĩa là bạn có thể khôi phục dữ liệu về bất kỳ thời điểm nào từ 5 phút trước cho đến khi kết thúc thời gian lưu giữ backup.

---

**Ví dụ**

Để giúp bạn bắt đầu, dưới đây là các liên kết mã ví dụ. Bao gồm cách kết nối với Amazon DocumentDB bằng nhiều ngôn ngữ lập trình phổ biến, mã từ blog và mẫu AWS Lambda.

-   [Cách kết nối đến Amazon DocumentDB bằng nhiều ngôn ngữ lập trình phổ biến](https://docs.aws.amazon.com/documentdb/latest/developerguide/connect.html).
-   [Mẫu hàm AWS Lambda](https://github.com/aws-samples/amazon-documentdb-samples/tree/master/lambda).
-   [Mã ví dụ từ các bài blog khác](https://github.com/aws-samples/amazon-documentdb-samples/tree/master/blogs).
-   [Kho GitHub chính thức của Amazon DocumentDB Samples](https://github.com/aws-samples/amazon-documentdb-samples).

---

**Tổng kết**

Trong bài viết này, chúng ta đã thảo luận về các thực hành tốt nhất (best practices) trong việc quản lý và tối ưu cụm Amazon DocumentDB. Nhiều nhà phát triển game đang sử dụng Amazon DocumentDB để đơn giản hóa thiết kế và quản lý hệ thống cơ sở dữ liệu backend vận hành trò chơi của họ. Bằng cách áp dụng các thực hành được nêu trong bài viết này, bạn có thể bắt đầu thuận lợi và triển khai thành công Amazon DocumentDB.

Để tìm hiểu thêm về Amazon DocumentDB, bạn có thể theo dõi các video trong **Amazon DocumentDB Insider Hour**, nơi chia sẻ thông tin chi tiết về kiến trúc tốt (well-architected lens), workshop, quy trình di chuyển (migration) và các bản phát hành mới. Ngoài ra, bạn có thể truy cập GitHub của **Amazon DocumentDB Tools** để sử dụng trong quá trình đánh giá và di chuyển dữ liệu.

---

### Về các tác giả

| Hình ảnh                                                       | Thông tin                                                                                                                                                                                                                          |
| :------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![Jackie Jiang](/images/3-BlogsTranslated/Blog4/author1.jpg)   | **Jackie Jiang**: Jackie là Senior Database Specialist Solutions Architect tại AWS. Cô làm việc với các khách hàng quan trọng về chiến lược cơ sở dữ liệu, di chuyển cơ sở dữ liệu và các thực tiễn tốt nhất về Amazon DocumentDB. |
| ![Douglas Bonser](/images/3-BlogsTranslated/Blog4/author2.jpg) | **Douglas Bonser**: Douglas là Senior Solutions Architect tại AWS, chuyên hỗ trợ khách hàng Game Tech. Anh có nền tảng về phát triển phần mềm và đam mê giúp các studio game xây dựng và mở rộng trò chơi của họ trên AWS.         |
| ![Matthew Nimmo](/images/3-BlogsTranslated/Blog4/author3.jpg)  | **Matthew Nimmo**: Matthew là Sr. Solutions Architect tại AWS. Anh làm việc với các công ty game lớn nhất thế giới để giúp họ xây dựng, triển khai và mở rộng trò chơi trên đám mây.                                               |
