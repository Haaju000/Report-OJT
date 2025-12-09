---
title: "Deploy .NET Backend with AWS Elastic Beanstalk"
weight: 2
chapter: false
pre: " <b> 5.2 </b> "
---



#### Overview

In this workshop, you will learn how to deploy a .NET 8.0 backend application for Coffee Cloud Platform to **AWS Elastic Beanstalk** via AWS Console. The API will be tested with integrated **Swagger UI**.

**AWS Elastic Beanstalk** is a platform-as-a-service (PaaS) with features:
- 🚀 Easy deployment via AWS Console
- ⚖️ Auto-scaling based on traffic
- 📊 Automatic monitoring and health checks
- 📦 Direct deployment from .NET publish
- 🆓 Free Tier: 750 hours/month (t3.micro)

#### Architecture

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

#### Contents

1. [Workshop Overview](5.2.1-overview/)
2. [Publish Application](5.2.2-publish-app/)
3. [Deploy to Elastic Beanstalk](5.2.3-deploy-beanstalk/)
4. [Testing with Swagger](5.2.4-testing/)

#### Completion Time
⏱️ Approximately **60-90 minutes**

#### Requirements
- ✅ Completed Workshop 1 (Amplify Frontend)
- ✅ AWS Account with Elastic Beanstalk permissions
- ✅ .NET SDK 8.0 installed
- ✅ Web browser to access AWS Console and Swagger

| Role | Permissions | Functions |
|------|-------------|-----------|
| **Customer** | Đặt hàng, xem lịch sử, tích điểm | Browse menu, Place orders, Track delivery, Redeem vouchers |
| **Shipper** | Xem đơn hàng, cập nhật trạng thái | Accept orders, Update delivery status, Navigate routes |
| **Admin** | Quản lý toàn bộ hệ thống | Manage products, View analytics, Manage users, Configure settings |
