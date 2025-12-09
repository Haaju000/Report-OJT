---
title: "Kiểm tra và xác minh"
weight: 5
chapter: false
pre: " <b> 5.1.5 </b> "
---



## 1. Kiểm tra chức năng

### 1.1 Kiểm tra tất cả các trang

-  Trang chủ tải đúng
-  Menu hiển thị sản phẩm
-  Form đăng nhập hiển thị
-  Navigation hoạt động
-  Footer hiển thị

### 1.2 Kiểm tra Routing

Kiểm tra các URLs:
```
https://main.d3djm3hylbiyyu.amplifyapp.com/
https://main.d3djm3hylbiyyu.amplifyapp.com/menu
https://main.d3djm3hylbiyyu.amplifyapp.com/login
```

Refresh mỗi trang → Không bị lỗi 404 ✅

## 2. Kiểm tra CI/CD

### 2.1 Kiểm tra Auto-Deploy

1. Thay đổi code
2. Commit và push trên Github Desktop
3. Xác minh auto-deploy kích hoạt
4. Kiểm tra deploy thành công

## 3. Dọn dẹp (Tùy chọn)

Nếu muốn xóa app để tránh chi phí:

1. Amplify Console → **Actions** → **Delete app**
2. Xác nhận xóa


