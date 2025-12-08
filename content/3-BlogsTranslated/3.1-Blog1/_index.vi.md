---
title: "Blog 1"
date: ""
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---


# Đại học California Irvine sao lưu hàng petabyte dữ liệu nghiên cứu lên AWS

University of California, Irvine (UCI) đã dùng rclone kết hợp với các dịch vụ Amazon Web Services (như Amazon S3, IAM, CloudWatch…) để thiết lập một hệ thống backup tập trung, bảo vệ hơn 5 PB dữ liệu nghiên cứu (hơn 250 triệu file) từ hàng trăm máy chủ ở nhiều phòng lab.

Hệ thống này cho phép sao lưu hàng ngày/lần incremental, đồng thời sử dụng chính sách lưu trữ dài hạn và công cụ giám sát để cân bằng giữa hiệu năng, bảo mật và chi phí — cung cấp mô hình sao lưu quy mô lớn và hiệu quả cho các môi trường nghiên cứu.
---

## Bối cảnh

- University of California, Irvine (UCI) có hàng ngàn phòng lab nghiên cứu riêng lẻ với máy chủ lưu trữ dữ liệu — tổng cộng khoảng 100 máy chủ với khoảng 10 PB dữ liệu cần sao lưu.

- Trước đó, các giải pháp sao lưu riêng lẻ không đáp ứng được yêu cầu về chi phí, quy mô, và khả năng quản lý tập trung.

## Giải pháp của UCI

- UCI phát triển một hệ thống sao lưu tập trung dùng công cụ mã nguồn mở rclone phối hợp với các dịch vụ của Amazon Web Services (AWS), gồm Amazon S3, Amazon S3 Glacier Deep Archive, AWS Identity and Access Management (IAM), Amazon CloudWatch, Amazon Simple Notification Service (SNS), cùng các dịch vụ tự động hóa khác.

- Mỗi máy chủ nghiên cứu được phân quyền và cấu hình riêng biệt — với bucket S3 riêng, IAM role riêng, để đảm bảo tách biệt quyền quản trị và bảo mật.

- Hệ thống thực hiện sao lưu hàng ngày (incremental) và đồng bộ sâu mỗi tuần (deep sync), đồng thời dùng chính sách lifecycle để chuyển dữ liệu cũ sang lưu trữ dài hạn (Glacier Deep Archive), giúp giảm chi phí lưu trữ lâu dài.

- Toàn bộ quy trình — từ định nghĩa công việc (job), lên lịch (cron), sao lưu, bảo mật, giám sát, cảnh báo, đến khôi phục — đều được tự động hóa với mã Python do UCI phát triển.

## Kết quả

- Hệ thống đã sao lưu thành công hơn 5 PB dữ liệu, tương đương hơn 250 triệu file.

- UCI đạt được sự cân bằng giữa hiệu suất, bảo mật, chi phí và khả năng mở rộng: hệ thống có thể xử lý máy chủ từ vài TB đến vài PB, mà vẫn giữ được vận hành ổn định.

- Giải pháp này giúp UCI có lộ trình rõ ràng, quản lý tập trung, và có thể nhân rộng cho các đơn vị khác nếu cần.

## Ý nghĩa và gợi ý

- Với các tổ chức nghiên cứu hoặc doanh nghiệp có khối lượng dữ liệu lớn, phương pháp của UCI — kết hợp rclone + AWS + tự động hóa — là một mẫu tham chiếu hiệu quả để sao lưu dữ liệu ở quy mô petabyte.

- Việc tách biệt quản trị (sysadmin) và quản lý cloud (cloudadmin) giúp tăng cường bảo mật và giảm rủi ro do sai sót.

- Cơ chế sao lưu incremental + lifecycle storage giúp tối ưu chi phí lưu trữ dài hạn — phù hợp với dữ liệu nghiên cứu hoặc lưu trữ lâu dài.