---
title: "Deploy lên AWS Amplify"
weight: 4
chapter: false
pre: " <b> 5.1.4 </b> "
---



Trong bước này, chúng ta sẽ kết nối GitHub repository với AWS Amplify và deploy ứng dụng.

## 1. Truy cập AWS Amplify Console

### 1.1 Đăng nhập AWS Console

1. Truy cập [https://console.aws.amazon.com](https://console.aws.amazon.com)
2. Đăng nhập với tài khoản AWS
3. Chọn region: **US East (N. Virginia) us-east-1** (hoặc region bạn muốn)

### 1.2 Mở AWS Amplify

1. Trong thanh tìm kiếm, gõ "**Amplify**"
2. Click **AWS Amplify**

---

## 2. Tạo App mới

### 2.1 Bắt đầu với Amplify Hosting

1. Click **Get Started** trong phần **Amplify Hosting**
2. Hoặc click **New app** → **Host web app**

### 2.2 Chọn Git provider

1. Chọn **GitHub**
2. Click **Continue**

### 2.3 Cấp quyền GitHub

1. Click **Authorize AWS Amplify**
2. Đăng nhập GitHub nếu được yêu cầu
3. Cấp quyền cho AWS Amplify

{{% notice info %}}
📝 **Lưu ý**: AWS Amplify cần quyền truy cập repository để pull code và thiết lập webhooks
{{% /notice %}}

---

## 3. Thêm Repository

### 3.1 Chọn Repository

1. **Repository**: Chọn `coffee-cloud-frontend`
2. **Branch**: Chọn `main`
3. Click **Next**

### 3.2 Cấu hình Build Settings

AWS Amplify sẽ tự động phát hiện build settings cho Vite project:

```yaml
version: 1
frontend:
  phases:
    preBuild:
      commands:
        - npm ci
    build:
      commands:
        - npm run build
  artifacts:
    baseDirectory: dist
    files:
      - '**/*'
  cache:
    paths:
      - node_modules/**/*
```

{{% notice tip %}}
💡 **Mẹo**: Amplify tự động phát hiện framework. Nếu không đúng, bạn có thể chỉnh build settings sau
{{% /notice %}}

#### Kiểm tra settings:
- ✅ **App name**: `coffee-cloud-frontend`
- ✅ **Environment name**: `main`
- ✅ **Build command**: `npm run build`
- ✅ **Build output directory**: `dist`

Click **Next**

---

## 4. Cấu hình Advanced Settings (Tùy chọn)

### 4.1 Environment Variables

Hiện tại không cần, nhưng trong tương lai bạn có thể thêm:
- `VITE_API_URL`: URL của backend API
- `VITE_COGNITO_USER_POOL_ID`: ID của Cognito User Pool (Workshop 2)
- `VITE_COGNITO_CLIENT_ID`: Client ID của Cognito (Workshop 2)

Click **Next** để bỏ qua

### 4.2 Review

Kiểm tra lại tất cả settings:
- Repository: `your-username/coffee-cloud-frontend`
- Branch: `main`
- Build command: `npm run build`
- Output directory: `dist`

Click **Save and deploy**

---

## 5. Theo dõi quá trình Deployment

AWS Amplify sẽ bắt đầu deploy với 4 giai đoạn:

### 5.1 Provision
⏳ **Thời gian**: ~30 giây
- Phân bổ tài nguyên
- Thiết lập môi trường build

### 5.2 Build
⏳ **Thời gian**: ~2-3 phút
- Pull code từ GitHub
- Chạy `npm ci` (cài đặt dependencies)
- Chạy `npm run build`
- Tạo static files trong `dist/`

### 5.3 Deploy
⏳ **Thời gian**: ~30 giây
- Upload build artifacts lên CloudFront CDN
- Cấu hình SSL certificate
- Thiết lập domain

### 5.4 Verify
⏳ **Thời gian**: ~10 giây
- Health check
- Xác minh deployment thành công

---

## 6. Truy cập ứng dụng

### 6.1 Lấy URL

Sau khi deployment thành công:
1. Amplify sẽ hiển thị URL dạng: `https://main.xxxxxx.amplifyapp.com`
2. Click vào URL để mở ứng dụng

### 6.2 Kiểm tra ứng dụng

Kiểm tra tất cả trang:
- ✅ Trang chủ (`/`)
- ✅ Trang thực đơn (`/menu`)
- ✅ Trang đặt hàng (`/order`)
- ✅ Trang đăng nhập (`/login`)
- ✅ Navigation hoạt động
- ✅ Responsive design trên mobile

---

## 7. Thiết lập CI/CD Auto-Deploy

### 7.1 Kiểm tra Webhook

AWS Amplify đã tự động thiết lập webhook trong GitHub:

1. Vào GitHub repository → **Settings** → **Webhooks**
2. Bạn sẽ thấy webhook từ AWS Amplify

### 7.2 Kiểm tra Auto-Deploy

Hãy kiểm tra CI/CD pipeline:

1. Chỉnh sửa file `src/pages/Home.jsx` local
2. Thay đổi tiêu đề:
```jsx
<h1 className="display-4">☕ Chào mừng đến Coffee Cloud v2.0!</h1>
```

3. Commit và push:
```powershell
git add src/pages/Home.jsx
git commit -m "Update homepage heading"
git push
```

4. Quay lại **Amplify Console** → Bạn sẽ thấy build tự động kích hoạt!
5. Sau ~3 phút, làm mới app URL → Thấy thay đổi!

🎉 **CI/CD đã hoạt động!**

---

## 8. Xem Build Logs

### 8.1 Truy cập Logs

1. Trong Amplify Console, click vào **latest build**
2. Mở rộng các phases để xem logs:
   - **Provision logs**: Phân bổ tài nguyên
   - **Build logs**: npm install + build output
   - **Deploy logs**: Upload lên CDN
   - **Verify logs**: Health checks

### 8.2 Tải Logs

Click **Download build logs** để lưu logs về máy

---

## 9. Cấu hình Custom Domain (Tùy chọn)

### 9.1 Thêm Custom Domain

1. Trong Amplify Console, click **Domain management** (thanh bên)
2. Click **Add domain**
3. Nhập domain của bạn (ví dụ: `coffeecloud.com`)
4. Làm theo hướng dẫn để:
   - Thêm CNAME record vào DNS
   - Xác minh quyền sở hữu domain
   - Chờ SSL certificate (15-30 phút)



---

## 10. Monitoring & Metrics

### 10.1 Xem Analytics

1. Trong Amplify Console, click **Analytics** (thanh bên)
2. Xem:
   - **Requests**: Số lượng requests
   - **Data transferred**: Sử dụng băng thông
   - **Build minutes**: Sử dụng CI/CD
   - **Errors**: Lỗi 404, 500

### 10.2 Thiết lập Alarms (Tùy chọn)

1. Click **Alarms** → **Create alarm**
2. Cấu hình ngưỡng (ví dụ: Build failed > 2 lần)
3. Thêm thông báo email

---

## 11. Xử lý sự cố

### Vấn đề 1: Build Failed - "npm: command not found"

**Giải pháp**: Cập nhật build settings:
```yaml
version: 1
frontend:
  phases:
    preBuild:
      commands:
        - nvm use 18  # Chỉ định Node version
        - npm ci
```

### Vấn đề 2: "Module not found" error

**Giải pháp**: Xóa cache và rebuild:
1. Amplify Console → **App settings** → **Build settings**
2. Xóa cache
3. Redeploy

### Vấn đề 3: 404 khi refresh route

**Giải pháp**: Thêm redirects cho SPA:
1. Click **Rewrites and redirects**
2. Thêm rule:
   - Source: `</^[^.]+$|\.(?!(css|gif|ico|jpg|js|png|txt|svg|woff|ttf)$)([^.]+$)/>`
   - Target: `/index.html`
   - Type: `200 (Rewrite)`

---

## Bước tiếp theo

Tiếp tục với [Testing](../5.1.5-testing/).
