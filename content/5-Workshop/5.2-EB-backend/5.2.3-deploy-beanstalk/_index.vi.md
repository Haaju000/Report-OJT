---
title: "Triển khai lên AWS Elastic Beanstalk"
weight: 3
chapter: false
pre: " <b> 5.2.3 </b> "
---



Bây giờ hãy triển khai .NET API của bạn lên Elastic Beanstalk sử dụng AWS Console.

#### Bước 1: Truy cập Elastic Beanstalk Console

1. Đăng nhập vào [AWS Console](https://console.aws.amazon.com/)
2. Tìm **"Elastic Beanstalk"** trong thanh tìm kiếm phía trên
3. Click **Elastic Beanstalk** service

#### Bước 2: Tạo Application Mới

1. Click nút **"Create Application"**
2. Điền thông tin application

#### Bước 3: Cấu hình Environment

**Environment information:**
![Select GitHub](/images/5-Workshop/env-eb.png)

**Platform:**
- **Platform:** `.NET on Windows Server`
- **Platform branch:** `.NET 8 running on 64bit Windows Server 2022`
- **Platform version:** Latest (Khuyến nghị)

#### Bước 4: Upload Application Code

**Application code:**
- Chọn **"Upload your code"**
- **Version label:** `v1.0.0` (hoặc ngày hiện tại như `2025-12-08`)
- **Source code origin:** Choose file
- Click **"Choose file"** và chọn file `publish.zip` của bạn

⚠️ **Quan trọng:** Đảm bảo bạn upload file ZIP, không phải thư mục!

#### Bước 5: Cấu hình Service Access

**Service role:**
- Nếu lần đầu: Click **"Create and use new service role"**
- Role name: `aws-elasticbeanstalk-service-role` (tự động tạo)

**EC2 key pair (tùy chọn):**
- Chọn existing hoặc bỏ qua (không cần cho deployment cơ bản)

**EC2 instance profile:**
- Nếu lần đầu: Click **"Create new instance profile"**
- Dùng: `aws-elasticbeanstalk-ec2-role`

#### Bước 6: Thiết lập Networking (Tùy chọn)

**Virtual Private Cloud (VPC):**
- Dùng default VPC (khuyến nghị cho testing)

**Public IP address:**
- ✅ Activate (cần thiết cho truy cập internet)

Bỏ qua các tùy chọn networking khác.

#### Bước 7: Cấu hình Instance

**Instance types:**
- Chọn: `t3.micro` (Đủ điều kiện Free Tier!)
- Xóa các instance types khác

**Root volume:**
- Type: `General Purpose (SSD)`
- Size: `10 GB` (mặc định)

#### Bước 8: Cấu hình Auto-Scaling

**Environment type:**

**Cho Single Instance (Free Tier):**
- Chỉ 1 instance, không scaling
- Tốt cho testing/development

#### Bước 9: Cấu hình Health Monitoring

**Health reporting:**
- System: `Enhanced` (khuyến nghị)
![Select GitHub](/images/5-Workshop/health-eb.png)

#### Bước 10: Cấu hình Environment Properties

Cuộn xuống phần **Environment properties** và thêm:

![Select GitHub](/images/5-Workshop/env-eb.png)

#### Bước 11: Review và Create

1. Review tất cả cài đặt
2. Click **"Submit"**
3. Đợi environment được tạo (5-10 phút)

Bạn sẽ thấy:
- 🔄 **Creating environment** (vàng)
- 🔄 **Launching instances**
- 🔄 **Running deployment**
- ✅ **Environment created successfully** (xanh)

#### Bước 12: Lấy API URL

Sau khi deployment hoàn tất:

1. Bạn sẽ thấy domain ở phía trên:
   ```
   http://coffeecloud-api-env.ap-southeast-1.elasticbeanstalk.com
   ```

2. **Test Swagger UI:**
   ```
   http://coffeecloud-api-env.ap-southeast-1.elasticbeanstalk.com/swagger
   ```

**Định dạng domain ví dụ:**
```
http://[environment-name].[region].elasticbeanstalk.com
http://fixenv-env.eba-vgperhwx.ap-southeast-1.elasticbeanstalk.com
```



#### Bước 14: Cấu hình CORS cho Amplify


Cập nhật `Program.cs` và redeploy:
```csharp
builder.Services.AddCors(options =>
{
    options.AddPolicy("AllowAll", policy =>
    {
        policy.WithOrigins("http://localhost:3000",
                "https://main.d3djm3hylbiyyu.amplifyapp.com",
               "http://fixenv-env.eba-vgperhwx.ap-southeast-1.elasticbeanstalk.com")
              .AllowAnyMethod()
              .AllowAnyHeader()
  .AllowCredentials();
    });
});
```

#### Các Vấn đề Thường gặp

**Vấn đề: Environment health màu đỏ/degraded**
- Kiểm tra CloudWatch Logs: Configuration → Software → View logs
- Xác minh phiên bản .NET 8.0 SDK
- Kiểm tra `web.config` có trong ZIP không

**Vấn đề: 502 Bad Gateway**
- Application không khởi động
- Kiểm tra logs cho .NET errors
- Xác minh tất cả dependencies có đủ

**Vấn đề: Không truy cập được /swagger**
- Kiểm tra Swagger có bật trong production không
- Xác minh app chạy đúng port (5000)
- Kiểm tra security group cho phép HTTP traffic

**Vấn đề: CORS errors từ frontend**
- Cập nhật CORS policy trong `Program.cs`
- Thêm domain Amplify vào allowed origins
- Redeploy với cài đặt đã cập nhật

#### Giám sát Application của bạn

**CloudWatch Logs:**
1. Configuration → Software
2. Click **"CloudWatch logs"**
3. Xem application logs và errors

**Metrics:**
1. Tab Monitoring
2. Xem CPU, Memory, Network usage
3. Thiết lập alarms cho high usage

**Health:**
1. Dashboard chính hiển thị health status
2. Xanh = Healthy
3. Vàng = Warning
4. Đỏ = Degraded/Severe

#### Tối ưu Chi phí

**Free Tier Usage:**
- 1 t2.micro instance: FREE
- Load Balancer: ~$16/tháng
- Data transfer: 15GB free/tháng

**Để Ở trong Free Tier:**
- Dùng environment type **Single instance**
- Giữ 1 t2.micro instance
- Giám sát data transfer

**Để Scale Up (Khi Sẵn sàng):**
- Chuyển sang Load Balanced
- Tăng min/max instances
- Bật auto-scaling

**Tiếp theo:** Hãy test tất cả API endpoints với Swagger! →

