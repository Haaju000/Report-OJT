---
title: "Yêu cầu trước khi bắt đầu"
weight: 2
chapter: false
pre: " <b> 5.1.2 </b> "
---



Trước khi bắt đầu workshop, hãy đảm bảo bạn đã chuẩn bị đầy đủ các yêu cầu sau:

## 1. Tài khoản AWS

### 1.1 Thiết lập cảnh báo Billing

1. Đăng nhập **AWS Console**: [https://console.aws.amazon.com](https://console.aws.amazon.com)
2. Click vào tên tài khoản (góc phải trên) → **Billing Dashboard**
3. Ở thanh bên, chọn **Billing Preferences**
4. Bật:
   - **Receive Free Tier Usage Alerts**
   - **Receive Billing Alerts**
5. Click **Save preferences**

### 1.2 Tạo CloudWatch Billing Alarm

1. Trong **Billing Dashboard**, click **Budgets** (thanh bên)
2. Click **Create budget**
3. Chọn **Cost budget - Recommended**
4. Cấu hình:
   - Budget name
   - Budgeted amount
   - Budget scope: All AWS services
5. Click **Create budget**

---

## 2. AWS CLI (Tùy chọn - Khuyến nghị)

### 2.1 Cài đặt AWS CLI

#### Windows:
```bash
msiexec.exe /i https://awscli.amazonaws.com/AWSCLIV2.msi
```

### 2.2 Cấu hình AWS CLI

```bash
aws configure
```

Nhập:
- AWS Access Key ID: (Secret Key)
- AWS Secret Access Key: (Secret Key)
- Default region: `ap-southeast-1`
- Default output format: `json`

---

## Bước tiếp theo

Tiếp tục với [Cài đặt Github Repository](../5.1.3-setup-git/) để tạo ứng dụng Coffee Cloud.
