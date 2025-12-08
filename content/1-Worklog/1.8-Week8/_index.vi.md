---
title: "Worklog Tuần 8"
date: ""
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---


### Mục tiêu tuần 8:

* Hiểu và vận hành AWS Lambda: cơ chế runtime, handler, timeout và các event trigger (đặc biệt là S3).
* Xây dựng và triển khai API Gateway kết nối Lambda, tạo REST API cơ bản.
* Thiết lập IAM Role và CloudWatch Logs để đảm bảo Lambda hoạt động an toàn, có theo dõi và giám sát đầy đủ.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2  | - Cơ bản về hàm Lambda    <br>    - Trình xử lý, thời gian chạy, thời gian chờ                | 27/09/2025 | 27/09/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3  | - Kích hoạt S3 → Sự kiện Lambda                                                               | 28/09/2025 | 28/09/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4  | - Cổng API → Lambda   <br>   - Tạo API REST                                                   | 29/09/2025 | 29/09/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5  | - Vai trò IAM cho Lambda  <br>    - Ghi nhật ký CloudWatch                                    | 30/09/2025 | 30/09/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6  | - **Thực hành:**    <br>    + API Gateway → Lambda → DynamoDB <br> + Nhật ký với CloudWatch   | 31/09/2025 | 31/09/2025 | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 8:

* Triển khai thành công Lambda function với đúng runtime, handler và xử lý được sự kiện từ S3.

* Xây dựng được REST API bằng API Gateway kết nối Lambda và hoạt động ổn định.

* Cấu hình IAM Role + CloudWatch Logs giúp Lambda chạy đúng quyền và theo dõi log đầy đủ.