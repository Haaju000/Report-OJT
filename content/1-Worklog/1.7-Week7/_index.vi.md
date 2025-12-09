---
title: "Worklog Tuần 7"
date: ""
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---



### Mục tiêu tuần 7:

* Hiểu và triển khai được hệ thống phân phối tải và mở rộng tự động bằng cách sử dụng ALB/NLB, Target Group và Auto Scaling Group.
* Thiết lập được cơ chế scaling tự động (scheduled và dynamic) để hệ thống tự tăng/giảm số lượng EC2 theo tải thực tế.
* Thực hiện hoàn chỉnh bài lab ALB + ASG, bao gồm cấu hình health check và tự động scale khi CPU vượt ngưỡng (>60%).

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2 | - Elastic Load Balancer (ALB, NLB)     <br>    - Tạo ALB                                  | 20/10/2025 | 20/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3 | - Nhóm mục tiêu    <br>    - Kiểm tra tình trạng                                          | 21/10/2025 | 21/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Nhóm Tự động Điều chỉnh Quy mô (ASG)     <br>    - Khởi chạy Mẫu                        | 22/10/2025 | 22/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Chính sách Điều chỉnh Quy mô     <br>    - Điều chỉnh Quy mô Theo lịch trình & Động     | 23/10/2025 | 23/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - **Thực hành:** <br> + ALB + ASG  <br>    + Tự động điều chỉnh tỷ lệ khi CPU > 60%       | 24/10/2025 | 24/10/2025 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 7:

* Triển khai thành công ALB và ASG, giúp hệ thống có khả năng phân phối tải và tự mở rộng theo nhu cầu.

* Cấu hình đúng Target Group và Health Check, đảm bảo chỉ gửi traffic đến các EC2 khỏe mạnh.

* Thiết lập và kiểm thử Scaling Policies, cho phép EC2 tự động scale khi CPU > 60% và hoạt động ổn định theo điều kiện tải.