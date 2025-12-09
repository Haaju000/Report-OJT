---
title: "Publish Ứng dụng .NET để Triển khai"
weight: 2
chapter: false
pre: " <b> 5.2.2 </b> "
---



Trước khi triển khai lên Elastic Beanstalk, chúng ta cần publish ứng dụng .NET thành package triển khai.


#### Bước 2: Publish lên AWS trên Visual Code Studio (Elastic Beanstalk)

![Select GitHub](/images/5-Workshop/publish-be.png)

Lệnh này tạo thư mục `publish` với tất cả files cần thiết.

#### Bước 3: Tự động tạo file Zip và deploy
![Select GitHub](/images/5-Workshop/auto-deploy.png)

Tạo file ZIP từ output đã publish

Cách thứ hai là dùng lệnh này để republish và rezip. Sau đó upload lên Elastic Beanstalk Console:
```bash
dotnet publish -c Release -o ./publish
# Copy Procfile vào thư mục publish
Copy-Item Procfile .\publish\
Compress-Archive -Path .\publish\* -DestinationPath CoffeeCloudAPI.zip -Force
```

#### Deployment Package Sẵn sàng! 📦

Bây giờ bạn có:
- ✅ `CoffeeShopAPI.zip` - Sẵn sàng upload lên Elastic Beanstalk
- ✅ Swagger UI đã bật để testing
- ✅ Tất cả dependencies đã bao gồm
- ✅ Các file cấu hình phù hợp

**Vị trí File:**

![Select GitHub](/images/5-Workshop/publish-file.png)

#### Các Vấn đề Thường gặp

**Vấn đề:** File ZIP quá lớn (>512 MB)
**Giải pháp:** 
- Xóa các file không cần thiết khỏi thư mục publish
- Kiểm tra các dependency bị trùng lặp
- Dùng `dotnet publish --self-contained false`

**Vấn đề:** Swagger không hoạt động sau khi deploy
**Giải pháp:**
- Đảm bảo `UseSwagger()` được gọi không có điều kiện môi trường
- Xác minh `appsettings.json` có trong ZIP
- Kiểm tra cài đặt HTTPS redirection

**Vấn đề:** Ứng dụng không khởi động
**Giải pháp:**
- Xác minh `web.config` có mặt
- Kiểm tra phiên bản .NET khớp (8.0)
- Xem CloudWatch logs sau khi deploy

#### Bước tiếp theo

Bây giờ chúng ta đã có deployment package, hãy upload lên AWS Elastic Beanstalk! →

