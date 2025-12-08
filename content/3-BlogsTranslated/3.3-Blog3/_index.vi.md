---
title: "Blog 3"
date: ""
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---



# Tăng cường khả năng quan sát giới hạn API với Amazon QuickSight

Bài viết hướng dẫn cách dùng Amazon QuickSight để tạo một dashboard tập trung, giúp bạn tổng hợp và hiển thị dữ liệu phân mảnh về throttling API từ nhiều tài khoản và vùng (region) khác nhau của Amazon Web Services.

Nhờ đó bạn có thể dễ dàng theo dõi API nào bị throttle, ở tài khoản/vùng nào, từ đó đánh giá tác động, điều chỉnh tần suất gọi API và cải thiện logic retry để tối ưu hoạt động.

---

## Bối cảnh

- Bài viết Amazon QuickSight (QuickSight) của Amazon Web Services (AWS), với tiêu đề Enhance API throttling visibility with Amazon QuickSight, đề cập đến việc dùng QuickSight để giúp các tổ chức có nhiều tài khoản AWS và nhiều vùng (region) có thể theo dõi và hiển thị thông tin throttling API một cách tập trung.

- “Throttling” ở đây nghĩa là khi các API của AWS vượt mức giới hạn rate limit — gây ra lỗi trả về (error), có thể dẫn tới retry, gián đoạn hệ thống, hoặc chi phí phát sinh nếu không được kiểm soát.

## Giải pháp và kiến trúc

- Giải pháp sử dụng mô hình hub-and-spoke: một tài khoản “data-collection” làm hub để gom dữ liệu từ nhiều tài khoản AWS khác (spokes) ở nhiều Region.

- Khi API bị throttled trong bất kỳ tài khoản nào, sự kiện được ghi lại bởi AWS CloudTrail (với errorCode như Client.RequestLimitExceeded hoặc ThrottlingException) → gửi tới Amazon EventBridge → lọc ra event throttling → gửi vào một custom event bus ở tài khoản data-collection.

- Sau đó, các sự kiện này được chuyển qua Amazon Kinesis Data Firehose → lưu vào Amazon S3 → được catalog hóa bởi AWS Glue → rồi sử dụng Amazon Athena để query → dữ liệu được QuickSight dùng để hiển thị trên dashboard.

- Dashboard QuickSight tổng hợp thông tin: API nào bị throttled, dịch vụ AWS nào, tài khoản/Region nào, IAM user/role nào — giúp bạn nhìn rõ “bức tranh tổng” về throttling across toàn bộ tổ chức.

## Lợi ích và khi nào nên dùng

- Cho phép giám sát tập trung — thay vì phải kiểm tra riêng lẻ từng tài khoản/region, bạn có một dashboard chung.

- Giúp đánh giá tác động throttling tổng thể: biết API nào, region nào bị throttled nhiều, từ đó điều chỉnh rate, retry logic, hoặc thiết kế lại workflow để tránh lãng phí hoặc lỗi.

- Hữu ích đặc biệt với tổ chức lớn, nhiều tài khoản AWS hoặc nhiều vùng, nhiều dịch vụ — nơi việc theo dõi thủ công gần như bất khả thi.

- Giúp cải thiện reliability, giảm lỗi do throttling, kiểm soát chi phí và tối ưu hiệu suất sử dụng API.

## Một vài điều cần lưu ý và yêu cầu

- Cần QuickSight Enterprise Edition + đủ dung lượng SPICE để lưu và xử lý dữ liệu.

- Phải có quyền deploy AWS CloudFormation / StackSets để triển khai tài nguyên (EventBridge, Firehose, S3, Glue, etc.) qua các tài khoản/region.

- Hiện giải pháp chỉ áp dụng cho các sự kiện quản lý API (management API calls) của CloudTrail, vì CloudTrail “data events” chưa hỗ trợ gửi đến EventBridge tại thời điểm viết bài.