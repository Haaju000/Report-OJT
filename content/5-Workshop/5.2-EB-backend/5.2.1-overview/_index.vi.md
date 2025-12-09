---
title: "Tổng quan Workshop"
weight: 1
chapter: false
pre: " <b> 5.2.1 </b> "
---



#### Bạn sẽ xây dựng gì

Trong workshop này, bạn sẽ tạo backend **Web API .NET 8.0** sẵn sàng cho production cho **Coffee Cloud Platform** và triển khai trực tiếp lên **AWS Elastic Beanstalk** qua **AWS Console**. API bao gồm **Swagger UI** để test và tài liệu hóa dễ dàng.

- ☕ **Quản lý Menu** - Lấy tất cả sản phẩm, lọc theo danh mục
- 🛒 **Xử lý Đơn hàng** - Tạo đơn hàng, cập nhật trạng thái, theo dõi đơn hàng
- 👤 **Quản lý Người dùng** - Vai trò Customer, Shipper, Admin
- 📊 **Phân tích** - Thống kê đơn hàng, báo cáo doanh thu
- 📝 **Swagger UI** - Tài liệu và testing API tương tác

#### Tổng quan Kiến trúc

```
┌─────────────────────────────────────────────────────┐
│           ReactJS Frontend (Amplify)                │
│   https://main.d3djm3hylbiyyu.amplifyapp.com/       │
└──────────────────┬──────────────────────────────────┘
                   │ HTTPS API Calls
                   ▼
┌─────────────────────────────────────────────────────┐
│      Application Load Balancer (ALB)                │
│         - Kiểm tra sức khỏe                         │
│         - Kết thúc SSL                              │
└──────────────────┬──────────────────────────────────┘
                   │
        ┌──────────┴──────────┐
        ▼                     ▼
┌──────────────┐      ┌──────────────┐
│ EC2 Instance │      │ EC2 Instance │
│   (t3.micro) │      │   (t3.micro) │
│              │      │              │
│  .NET 8.0    │      │  .NET 8.0    │
│  Web API     │      │  Web API     │
│              │      │              │
│  + Swagger   │      │  + Swagger   │
└──────┬───────┘      └──────┬───────┘
       │                     │
       └──────────┬──────────┘
                  ▼
          ┌───────────────┐
          │   DynamoDB    │
          │               │
          │ - MenuItems   │
          │ - Orders      │
          │ - Users       │
          └───────────────┘
```

#### Công nghệ chính

| Công nghệ | Mục đích | Tại sao? |
|-----------|----------|----------|
| **.NET 8.0** | Framework Web API | Hiện đại, nhanh, đa nền tảng C# |
| **Swagger UI** | Tài liệu API | Testing tương tác, tài liệu tự động tạo |
| **Elastic Beanstalk** | Dịch vụ Platform | Tự động mở rộng, cân bằng tải, giám sát |
| **DynamoDB** | Cơ sở dữ liệu NoSQL | Serverless, mở rộng, độ trễ thấp |
| **CloudWatch** | Giám sát | Logs, metrics, alarms |


#### Ước tính Chi phí

**Đủ điều kiện Free Tier:**
- Elastic Beanstalk: Không tính phí bổ sung
- EC2 t3.micro: 750 giờ/tháng (1 instance = miễn phí)
- DynamoDB: 25 GB storage, 25 WCU/RCU
- Data Transfer: 15 GB/tháng outbound

**Sau Free Tier:**
- 2 x t3.micro instances: ~$16/tháng
- Application Load Balancer: ~$16/tháng
- DynamoDB: Trả theo sử dụng (~$1-5/tháng cho apps nhỏ)


