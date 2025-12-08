---
title: "Blog 2"
date: ""
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---



# Kiến trúc sư HPC tiết kiệm – đảm bảo hiệu quả FinOps cho khối lượng công việc HPC ở quy mô lớn

Bài viết nhấn mạnh rằng khi dùng Amazon Web Services (AWS) để chạy các workload HPC, bạn cần coi chi phí như một “yêu cầu không chức năng” — cân bằng giữa hiệu năng và chi phí để tránh lãng phí.

Để tiết kiệm, họ khuyến nghị dùng các biện pháp như: chọn instance phù hợp, dùng EC2 Spot hoặc Savings Plan, tối ưu sử dụng CPU/ bộ nhớ/ storage, và theo dõi sát năng suất & chi phí bằng công cụ observability.

---

## Bối cảnh

- Bài Amazon Web Services (AWS) — “The frugal HPC architect – ensuring effective FinOps for HPC workloads at scale” phân tích cách áp dụng nguyên tắc của Werner Vogels (The Frugal Architect) vào các workload hiệu năng cao (HPC) khi chạy trên cloud.

- Mục tiêu giúp các tổ chức dùng HPC trên đám mây vẫn đảm bảo được hiệu suất, khả năng mở rộng, linh hoạt — đồng thời kiểm soát chi phí một cách chặt chẽ và hiệu quả.

## Những nguyên tắc và cách làm chính

- Chi phí cần được xem là “yêu cầu phụ” (non-functional requirement) — bên cạnh bảo mật, khả năng mở rộng, hiệu quả, v.v. Không nên coi chi phí là sau cùng mới tính.

- Giảm “đơn vị tiêu dùng” (unit consumption).

- Với storage / I/O-intensive workload: thay vì giữ toàn bộ data trên hệ thống “fast storage”, có thể dùng giải pháp hybrid: ví dụ liên kết hệ thống lưu trữ hiệu năng cao với object storage và tải dữ liệu theo demand, hoặc dùng cache, và chỉ giữ dữ liệu cần thiết.

## Quan sát và đo lường

- Theo nguyên tắc “Unobserved systems lead to unknown costs”: Nếu bạn không theo dõi, đo lường rõ ràng — sẽ không biết chi phí thực và không phát hiện được lãng phí.

- Cần có hệ thống metrics + logs + tracing để đo: tỷ lệ compute thực / tổng capacity, chi phí so với giá trị tạo ra, phân tích usage, bất thường… AWS cung cấp công cụ như Amazon CloudWatch, AWS Compute Optimizer, báo cáo usage/cost export, v.v.

- Nhờ đó, tổ chức có thể: xác định resource dư thừa, under-utilized; đánh giá xem workload có đáng chạy hay không; điều chỉnh cấu hình hoặc hạ tầng để tiết kiệm.

## Kết luận và ý nghĩa

- Khi di chuyển HPC từ on-premise sang cloud, chi phí không còn là giá cố định — nó phụ thuộc vào cách bạn thiết kế architecture, sử dụng, và quản lý. Việc “tiết kiệm cẩn trọng” (frugal) cần được coi là một phần thiết kế từ đầu.

- Với cách tiếp cận đúng: chọn instance phù hợp, tối ưu usage, dùng công cụ observability & FinOps — HPC trên cloud có thể vừa mạnh mẽ, linh hoạt, vừa quản lý chi phí hiệu quả. Điều này giúp các tổ chức, doanh nghiệp, hoặc viện nghiên cứu có workload cao (scientific simulation, AI/ML, xử lý dữ liệu lớn…) tận dụng cloud mà không “vỡ ngân sách”.

- Nguyên lý từ The Frugal Architect — “cost as non-functional requirement”, “efficiency & effectiveness”, “observability” — là tư duy nên áp dụng không chỉ cho HPC mà cho mọi hệ thống cloud-scale.