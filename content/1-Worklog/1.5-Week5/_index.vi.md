---
title: "Worklog Tuần 5"
date: ""
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---



### Mục tiêu tuần 5:

* Hiểu và triển khai được RDS (tạo database, cấu hình parameter/option group, kết nối từ EC2, thiết lập Backup – Multi-AZ – Read Replica).
* Sử dụng được DynamoDB, hiểu table structure (partition key, sort key) và tạo được bảng mẫu.
* Xây dựng một ứng dụng EC2 kết nối RDS, có backup tự động và tích hợp thêm 1 bảng DynamoDB để lưu dữ liệu thử nghiệm.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tổng quan về RDS    <br>    - Nhóm tham số, nhóm tùy chọn       | 06/09/2025 | 06/09/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Tạo RDS MySQL/PostgreSQL    <br>    - Kết nối từ EC2            | 07/09/2025 | 07/09/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Sao lưu, đa vùng sẵn sàng, bản sao đọc                          | 08/09/2025 | 08/09/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - DynamoDB: bảng, khóa phân vùng, khóa sắp xếp                    | 09/09/2025 | 09/09/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Thực hành:** <br> + Ứng dụng trên EC2 → Kết nối RDS <br> + Cấu hình sao lưu tự động <br> + Tạo bảng DynamoDB mẫu            | 10/09/2025 | 10/09/2025 | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 5:

* Triển khai và vận hành thành công RDS: tạo database, cấu hình parameter/option group, kết nối từ EC2, và thiết lập được Backup – Multi-AZ – Read Replica.

* Xây dựng được ứng dụng chạy trên EC2 kết nối đến RDS và hoạt động ổn định với cơ chế backup tự động.

* Tạo và quản lý được bảng DynamoDB mẫu, hiểu rõ cách thiết kế partition key, sort key và cách truy cập dữ liệu cơ bản.