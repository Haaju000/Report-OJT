---
title: "Workshop"
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Coffee Cloud Platform - AWS Workshop Series

Các workshop thực hành xây dựng Coffee Shop Order Platform trên AWS từ đầu đến cuối.

## 🎯 Tổng quan Workshop

Trong series workshop này, bạn sẽ học cách xây dựng một ứng dụng web full-stack trên AWS, bao gồm frontend với ReactJS + Amplify và backend .NET API với Elastic Beanstalk.

**Coffee Cloud Platform** là một ứng dụng đặt hàng cà phê online với các tính năng:
- 🛒 Đặt hàng và thanh toán online
- 👥 Hệ thống phân quyền 3 nhóm: Customer, Shipper, Admin
- ⭐ Tích điểm và đổi voucher
- 📍 Theo dõi giao hàng real-time với GPS
- 📊 Dashboard quản lý cho Admin

---

## 📚 Series Workshop

### Workshop Cốt lõi

#### 1. [Deploy ReactJS Frontend với AWS Amplify](5.1-amplify-frontend/)
⏱️ **90 phút** | 🎯 **Beginner-Intermediate**

Tạo và deploy ứng dụng ReactJS lên AWS Amplify với CI/CD tự động từ GitHub. Học cách setup pipeline, configure build settings, và optimize performance.

**Bạn sẽ học:**
- Tạo React app với Vite
- Setup Git repository
- Deploy lên AWS Amplify
- Configure CI/CD pipeline
- Environment variables và build optimization

---

#### 2. [Deploy .NET Backend với AWS Elastic Beanstalk](5.2-EB-backend/)
⏱️ **60-90 phút** | 🎯 **Intermediate**

Deploy .NET 8.0 Web API lên AWS Elastic Beanstalk với Swagger UI. Học về publish application, ZIP deployment, và integration với frontend qua Cloudflare Tunnel.

**Bạn sẽ học:**
- Publish .NET 8.0 application
- Deploy lên Elastic Beanstalk qua AWS Console
- Test API với Swagger UI
- Setup Cloudflare Tunnel cho HTTPS
- Connect backend với Amplify frontend

---

## 📋 Yêu cầu Trước khi Bắt đầu

Trước khi bắt đầu, đảm bảo bạn có:
- ✅ AWS Account (Free Tier eligible)
- ✅ GitHub account
- ✅ Node.js 18+ và npm
- ✅ .NET 8.0 SDK
- ✅ Git installed
- ✅ Code editor (VS Code khuyến nghị)
- ✅ Hiểu biết cơ bản về React, JavaScript, và C#

---

## 💰 Ước tính Chi phí

Với **AWS Free Tier**, tổng chi phí workshops:

| Dịch vụ | Free Tier | Sau Free Tier |
|---------|-----------|---------------|
| **Amplify** | 1000 build minutes/tháng | $0.01/phút |
| **Elastic Beanstalk** | 750 giờ/tháng (t3.micro) | ~$10/tháng |
| **DynamoDB** | 25 GB storage | $0.25/GB |
| **CloudWatch** | 10 custom metrics | $0.30/metric |
| **Data Transfer** | 15 GB/tháng | $0.09/GB |

**Tổng ước tính chi phí:** $0-5/tháng trong giai đoạn học

---

## 🚀 Bắt đầu

Bắt đầu với [Workshop 1: Deploy Frontend với AWS Amplify](5.1-amplify-frontend/)

---

## 📖 Tài liệu Bổ sung

- [AWS Free Tier](https://aws.amazon.com/free/)
- [AWS Documentation](https://docs.aws.amazon.com/)
- [React Documentation](https://react.dev/)
- [.NET Documentation](https://learn.microsoft.com/en-us/dotnet/)
- [Coffee Cloud Proposal](../2-Proposal/)

---
