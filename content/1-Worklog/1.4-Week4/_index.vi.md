---
title: "Worklog Tuần 4"
date: ""
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---



### Mục tiêu tuần 4:

* Understand and apply basic networking concepts in AWS: VPC, CIDR, subnet, route table, IGW, NAT, Security Group and NACL.
* Design and deploy a complete network architecture including public subnet + EC2 and private subnet + EC2.
* Validate the architecture's performance by testing private EC2 accessing the Internet through NAT Gateway.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Khái niệm VPC, CIDR, IPv4, subnet <br>    - Public và Private subnet            | 29/08/2025   | 29/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Route Table   <br>    - Internet Gateway  <br> NAT Gateway                      | 30/08/2025   | 30/08/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Security Group vs NACL <br>   - **Thực hành**: tạo VPC mới + 2 subnet           | 01/09/2025   | 01/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Thực hành cấu hình mạng hoàn chỉnh   <br>&emsp;  + VPC <br>&emsp; + Public subnet + EC2 <br>&emsp; + Private subnet         | 02/09/2025   | 02/09/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Lab: <br>&emsp;  + Deploy 1 EC2 public, 1 EC2 private <br>&emsp; + Kiểm tra private EC2 có ra Internet bằng NAT        | 03/09/2025   | 03/09/2025      | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 4:

* Hiểu về kiến trúc mạng cơ bản của AWS: VPC, subnet, CIDR, route table, IGW, NAT, Security Group và NACL.

* Tự triển khai một hệ thống mạng đầy đủ gồm VPC, public subnet với EC2 public và private subnet với EC2 private.

* Cấu hình đúng đường đi mạng và chứng minh được EC2 private có thể truy cập Internet thông qua NAT Gateway.