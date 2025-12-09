---
title: "Deploy .NET Backend với AWS Elastic Beanstalk"
weight: 2
chapter: false
pre: " <b> 5.2 </b> "
---



#### Tổng quan

Trong workshop này, bạn sẽ học cách deploy ứng dụng backend .NET 8.0 cho Coffee Cloud Platform lên **AWS Elastic Beanstalk** thông qua **AWS Console**. API sẽ được test với **Swagger UI** tích hợp sẵn.

**AWS Elastic Beanstalk** là platform-as-a-service (PaaS) với những tính năng:
- 🚀 Deploy dễ dàng qua AWS Console
- ⚖️ Auto-scaling dựa trên traffic
- 📊 Monitoring và health checks tự động
- 📦 Deploy trực tiếp từ .NET publish
- 🆓 Free Tier: 750 giờ/tháng (t3.micro)

#### Kiến trúc

```
ReactJS Frontend (Amplify)
         ↓ HTTPS API calls
Application Load Balancer
         ↓
   EC2 Instances (Auto Scaling)
   Running .NET 8.0 API
         ↓
    DynamoDB
```

#### Nội dung

1. [Tổng quan Workshop](5.2.1-overview/)
2. [Publish Ứng dụng](5.2.2-publish-app/)
3. [Deploy lên Elastic Beanstalk](5.2.3-deploy-beanstalk/)
4. [Kiểm tra với Swagger](5.2.4-testing/)

#### Thời gian hoàn thành
⏱️ Khoảng **60-90 phút**

#### Yêu cầu
- ✅ Đã hoàn thành Workshop 1 (Amplify Frontend)
- ✅ Tài khoản AWS với quyền tạo Elastic Beanstalk
- ✅ .NET SDK 8.0 đã cài đặt
- ✅ Trình duyệt web để truy cập AWS Console và Swagger
