---
title: "Tổng quan Workshop"
weight: 1
chapter: false
pre: " <b> 5.1.1 </b> "
---



#### Mục tiêu Workshop

Sau khi hoàn thành workshop này, bạn sẽ có thể:
- ✅ Tạo ứng dụng ReactJS từ đầu
- ✅ Thiết lập Git repository và push code lên GitHub
- ✅ Kết nối GitHub repository với AWS Amplify
- ✅ Deploy ứng dụng với CI/CD tự động
- ✅ Truy cập ứng dụng qua HTTPS URL
- ✅ Hiểu về build process và environment variables

#### Coffee Cloud Frontend - Tính năng cơ bản

Trong workshop này, chúng ta sẽ tạo giao diện cơ bản cho Coffee Cloud Platform bao gồm:
- 🏠 **Trang chủ**: Giới thiệu về Coffee Cloud
- 📋 **Trang Menu**: Danh sách sản phẩm coffee
- 👤 **Trang Đăng nhập**: Trang đăng nhập (sẽ tích hợp Cognito ở Workshop 2)

#### Công nghệ sử dụng

- **Frontend Framework**: ReactJS 
- **Build Tool**: Create React App
- **Version Control**: Git + GitHub
- **Hosting**: AWS Amplify
- **CDN**: CloudFront (tự động từ Amplify)

#### Kiến trúc triển khai

```
┌─────────────────┐
│  Developer      │
│  (Máy tính)     │
└────────┬────────┘
         │ git push
         ▼
┌─────────────────┐
│  GitHub         │
│  Repository     │
└────────┬────────┘
         │ webhook trigger
         ▼
┌─────────────────┐
│  AWS Amplify    │
│  - Build        │
│  - Deploy       │
└────────┬────────┘
         │ phân phối
         ▼
┌─────────────────┐
│  CloudFront CDN │
│  (Toàn cầu)     │
└────────┬────────┘
         │ HTTPS
         ▼
┌─────────────────┐
│  Người dùng     │
└─────────────────┘
```

#### Quy trình CI/CD tự động

1. Developer push code lên GitHub
2. GitHub webhook kích hoạt AWS Amplify build
3. Amplify tự động:
   - Pull code từ GitHub
   - Chạy `npm install`
   - Chạy `npm run build`
   - Deploy build artifacts lên CloudFront CDN
4. Website tự động cập nhật (2-3 phút)

#### Chi phí dự kiến

Với **AWS Free Tier**, workshop này **hoàn toàn miễn phí**:
- ✅ 1000 build minutes/tháng (Free Tier)
- ✅ 15GB storage (Free Tier)
- ✅ 15GB data transfer out (Free Tier)

Sau khi hết Free Tier:
- Build: ~$0.01/phút
- Hosting: ~$0.15/GB lưu trữ/tháng
- Data transfer: ~$0.15/GB phục vụ

**Chi phí ước tính**: Dưới $1/tháng cho traffic nhỏ



{{% notice tip %}}
💡 **Mẹo:** Nên tạo Git repository trước khi bắt đầu code để có thể commit thường xuyên
{{% /notice %}}

#### Bước tiếp theo

Bắt đầu với [Yêu cầu trước khi bắt đầu](../5.1.2-prerequisites/) để chuẩn bị môi trường làm việc.
