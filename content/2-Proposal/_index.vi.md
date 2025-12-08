---
title: "Bản đề xuất"
weight: 2
chapter: false
pre: " <b> 2. </b> "
---


# Coffee Cloud – Coffee Shop Order Platform  
### Project Documentation

📄 **[Download Complete Project Proposal (Word Document)](/documents/Coffee-Cloud-Complete-Proposal.docx)**

---
### 1. Tóm tắt điều hành
Dự án "Coffee Cloud – Coffee Shop Order Platform" là nền tảng web giúp khách hàng đặt cà phê trực tuyến, tích điểm sau mỗi đơn hàng và đổi voucher ưu đãi.

Hệ thống hỗ trợ ba nhóm người dùng: Customer, Shipper, và Admin, nhằm tối ưu trải nghiệm đặt hàng, giao hàng và quản lý vận hành quán.

Ứng dụng Frontend được xây dựng bằng ReactJS, Backend bằng C#/.NET chạy trên AWS Elastic Beanstalk, và được triển khai hoàn toàn trên AWS Free Tier với các dịch vụ: Amplify (Hosting + CI/CD), Cognito (Authentication), Elastic Beanstalk (.NET Backend services), S3 Storage, DynamoDB, SNS (Notifications), SES (Email Service), IAM, và CloudWatch Logs.  

### 2. Tuyên bố vấn đề  
*Vấn đề hiện tại*  
Quán cà phê truyền thống gặp khó khăn trong việc quản lý đơn hàng đông đúc, khách hàng phải chờ đợi lâu để đặt hàng và nhận sản phẩm. Không có hệ thống tích điểm để khuyến khích khách hàng quay lại, và việc theo dõi trạng thái đơn hàng chưa minh bạch.

*Giải pháp*  
Nền tảng Coffee Cloud được xây dựng với kiến trúc cloud có khả năng mở rộng trên AWS, sử dụng ReactJS cho frontend được host trên Amplify, và các dịch vụ backend được containerized triển khai trên Elastic Beanstalk. Hệ thống cung cấp ba giao diện riêng biệt cho Customer (đặt hàng, tích điểm), Shipper (nhận và giao hàng), và Admin (quản lý tổng thể). Dữ liệu được lưu trữ trong DynamoDB cho hiệu suất cao với S3 cho static assets và Amazon Location Service cho theo dõi giao hàng. Authentication được quản lý bởi Cognito với hỗ trợ đa role. AWS SNS xử lý thông báo realtime về trạng thái đơn hàng, trong khi SES quản lý email communications. Xử lý thanh toán được tích hợp thông qua các payment gateway bên ngoài. Các tính năng chính bao gồm đặt hàng trực tuyến, hệ thống tích điểm, theo dõi đơn hàng thời gian thực với GPS, quản lý inventory, và hệ thống thông báo đa kênh.

*Lợi ích và hoàn vốn đầu tư (ROI)*  
Hệ thống giúp tăng doanh thu thông qua kênh online, giảm thời gian chờ đợi của khách hàng và tối ưu hóa quy trình vận hành. Chi phí triển khai thấp nhờ sử dụng AWS Free Tier, ước tính chi phí vận hành hàng tháng dưới $5 USD cho giai đoạn đầu. Hệ thống tích điểm giúp tăng tỷ lệ khách hàng quay lại, dự kiến tăng doanh thu 20-30% so với hình thức truyền thống. Thời gian hoàn vốn ước tính 3-6 tháng nhờ tiết kiệm chi phí nhân lực và tăng hiệu quả bán hàng.  

### 3. Kiến trúc giải pháp  
Coffee Cloud áp dụng kiến trúc containerized có khả năng mở rộng trên AWS để đảm bảo high availability và tiết kiệm chi phí. Frontend ReactJS được deploy trên AWS Amplify với tích hợp CI/CD tự động từ Git repository. Backend services được containerized và triển khai trên AWS Elastic Beanstalk để dễ dàng scaling và quản lý. Dữ liệu được lưu trữ trong DynamoDB cho hiệu suất cao, S3 cho static assets, và Amazon Location Service cho GPS tracking và tối ưu hóa giao hàng. Authentication và authorization được quản lý bởi Amazon Cognito với hỗ trợ đa role (Customer, Shipper, Admin). Các dịch vụ thanh toán bên ngoài được tích hợp để xử lý giao dịch an toàn.

![Coffee Cloud Platform Architecture](/images/2-Proposal/architecture_proposal.jpg)

*Dịch vụ AWS sử dụng*  
- *AWS Amplify*: Hosting frontend ReactJS với CI/CD pipeline tự động từ Git repository.  
- *AWS Elastic Beanstalk*: Containerized .NET Framework 8.0 backend services với auto-scaling và load balancing.  
- *Amazon DynamoDB*: NoSQL database lưu trữ dữ liệu users, orders, products, points.  
- *Amazon S3*: Lưu trữ static assets như hình ảnh sản phẩm, documents, và backup data.  
- *Amazon Location Service*: GPS tracking, geocoding, và tối ưu hóa tuyến đường giao hàng.  
- *Amazon Cognito*: Authentication và authorization cho 3 loại user roles.  
- *Amazon SNS*: Push notifications và SMS alerts cho trạng thái đơn hàng và promotions.  
- *Amazon SES*: Email service cho order confirmations, receipts và marketing campaigns.  
- *Cloudflare Tunnel*: Kết nối domain an toàn giữa Amplify frontend và Elastic Beanstalk backend sử dụng Quick Tunnel.  
- *Payment Gateway Integration*: Xử lý thanh toán bên ngoài cho các giao dịch an toàn.  
- *Amazon CloudWatch*: Monitoring và logging cho toàn bộ hệ thống.  
- *AWS IAM*: Quản lý permissions và security policies.  

*Thiết kế thành phần*  
- *Frontend Layer*: ReactJS application hosted trên Amplify với responsive design và Git-based CI/CD.  
- *Application Layer*: Containerized .NET Framework 8.0 services triển khai trên Elastic Beanstalk với auto-scaling capabilities.  
- *Network Layer*: Cloudflare Tunnel (Quick Tunnel) cung cấp kết nối domain an toàn giữa frontend và backend services.  
- *Data Storage Layer*: DynamoDB cho structured data, S3 cho file storage, Location Service cho GPS data.  
- *Authentication Layer*: Cognito User Pools quản lý users với 3 groups (Customer, Shipper, Admin).  
- *Communication Layer*: SNS cho real-time notifications, SES cho email communications.  
- *Payment Layer*: Tích hợp external payment gateways cho xử lý giao dịch an toàn.  
- *Monitoring Layer*: CloudWatch theo dõi performance, errors và usage metrics với IAM security controls.

### 4. Triển khai kỹ thuật  
*Các giai đoạn triển khai*  
Dự án Coffee Cloud được chia thành 4 giai đoạn chính trong vòng 3 tháng:  
1. *Nghiên cứu và thiết kế*: Phân tích yêu cầu business, thiết kế database schema, wireframe UI/UX và kiến trúc system (Tháng 1).  
2. *Setup Environment và Backend Development*: Cấu hình AWS services, phát triển containerized backend services, thiết lập DynamoDB tables và Elastic Beanstalk environment (Tháng 1-2).  
3. *Frontend Development*: Xây dựng ReactJS application, tích hợp với backend APIs, implement authentication flow với Cognito (Tháng 2).  
4. *Testing và Deployment*: Unit testing, integration testing, performance testing, deploy lên Amplify và Elastic Beanstalk với monitoring (Tháng 3).  

*Yêu cầu kỹ thuật*  
- *Frontend Requirements*: ReactJS với hooks, React Router cho navigation, Axios cho API calls, CSS frameworks (Bootstrap/Material-UI), responsive design cho mobile và desktop.  
- *Backend Requirements*: Containerized .NET Framework 8.0 services trên Elastic Beanstalk, Entity Framework Core cho data access, JWT authentication, exception handling và logging.  
- *Database Design*: DynamoDB tables cho Users, Products, Orders, OrderItems, Points, Vouchers với proper indexing và relationships.  
- *Location Services*: Amazon Location Service integration cho GPS tracking, geocoding, và route optimization.  
- *Payment Integration*: External payment gateway APIs cho xử lý giao dịch an toàn.  
- *Network Integration*: Cloudflare Tunnel (Quick Tunnel) cho kết nối domain an toàn giữa Amplify frontend và Elastic Beanstalk backend.  
- *DevOps Requirements*: Git version control, Amplify CI/CD pipeline, Elastic Beanstalk deployment, CloudWatch monitoring, IAM roles và policies cho security.  

### 5. Lộ trình & Mốc triển khai  
*Lịch trình dự án*  
- *Giai đoạn 1 (Tuần 1-4)*: Nghiên cứu và thiết kế hệ thống  
    - Phân tích yêu cầu business và technical  
    - Thiết kế database schema và API specifications  
    - Tạo wireframes và UI mockups  
    - Setup AWS account và cấu hình ban đầu  
- *Giai đoạn 2 (Tuần 5-8)*: Phát triển Backend và Infrastructure  
    - Tạo DynamoDB tables và configure indexes  
    - Phát triển containerized backend services với C#/.NET  
    - Setup Elastic Beanstalk environment và deployment  
    - Configure Cognito User Pools và Groups  
    - Tích hợp Amazon Location Service cho GPS tracking  
    - Setup payment gateway integration  
- *Giai đoạn 3 (Tuần 9-10)*: Phát triển Frontend  
    - Xây dựng ReactJS components và pages  
    - Implement authentication và authorization  
    - Tích hợp với backend APIs  
    - Responsive design cho mobile  
- *Giai đoạn 4 (Tuần 11-12)*: Testing và Deployment  
    - Unit testing và integration testing  
    - Deploy lên AWS Amplify  
    - Performance optimization và monitoring setup  
    - User acceptance testing và documentation  

### 6. Ước tính ngân sách  
Dự án Coffee Cloud được thiết kế để tận dụng tối đa AWS Free Tier trong giai đoạn đầu phát triển và testing.

### Chi phí hạ tầng  
*Dịch vụ AWS (Monthly)*  
- AWS Amplify: $0.00 USD (Free Tier: 1000 build minutes, 15GB storage)  
- AWS Elastic Beanstalk: $0.00 USD (Free Tier: t3.micro instance, 750 hours/month)  
- Amazon DynamoDB: $0.00 USD (Free Tier: 25GB storage, 25 RCU/WCU)  
- Amazon S3: $0.00 USD (Free Tier: 5GB standard storage)  
- Amazon Location Service: $0.00 USD (Free Tier: 5000 requests/month)  
- Amazon Cognito: $0.00 USD (Free Tier: 50,000 MAU)  
- Amazon SNS: $0.00 USD (Free Tier: 1M publications, 100,000 HTTP/HTTPS requests)  
- Amazon SES: $0.00 USD (Free Tier: 62,000 emails/month)  
- Amazon CloudWatch: $0.00 USD (Free Tier: 10 custom metrics, 5GB logs)  

*Chi phí sau Free Tier (Ước tính cho production)*  
- AWS Amplify: ~$1.00 USD/month (hosting + build minutes)  
- AWS Elastic Beanstalk: ~$15.00 USD/month (t3.small instance cho production)  
- Amazon DynamoDB: ~$1.25 USD/month (additional RCU/WCU)  
- Amazon Location Service: ~$2.00 USD/month (additional GPS requests)  
- Amazon SNS: ~$0.50 USD/month (additional notifications + SMS)  
- Amazon SES: ~$1.00 USD/month (additional emails beyond free tier)  
- Payment Gateway Fees: ~$5.00 USD/month (transaction processing fees)  

*Tổng ước tính*: $0.00 USD/month (Development), ~$25.75 USD/month (Production)  
*Chi phí phát triển*: Chỉ phát sinh chi phí nhân lực cho developer  

### 7. Đánh giá rủi ro  
*Ma trận rủi ro*  
- Vượt giới hạn Free Tier: Ảnh hưởng trung bình, xác suất trung bình  
- Lỗi integration giữa các AWS services: Ảnh hưởng cao, xác suất thấp  
- Performance issues với DynamoDB: Ảnh hưởng trung bình, xác suất thấp  
- Security vulnerabilities: Ảnh hưởng cao, xác suất thấp  

*Chiến lược giảm thiểu*  
- Chi phí: Thiết lập CloudWatch billing alerts, monitor usage daily  
- Integration: Thực hiện thorough testing, sử dụng AWS SAM cho local testing  
- Performance: Thiết kế proper DynamoDB indexes, implement caching strategies  
- Security: Follow AWS security best practices, regular security audits  

*Kế hoạch dự phòng*  
- Backup và recovery plan cho DynamoDB data  
- Fallback mechanisms cho critical functions  
- Manual operation procedures nếu hệ thống gặp sự cố  
- Communication plan với stakeholders khi có incidents  

### 8. Kết quả kỳ vọng  
*Cải tiến kỹ thuật*: Hệ thống Coffee Cloud hoàn chỉnh với khả năng xử lý hàng trăm đơn hàng đồng thời, responsive design hoạt động mượt mà trên mọi thiết bị.

*Lợi ích kinh doanh*:  
- Tăng 30% doanh thu nhờ kênh online mới  
- Giảm 50% thời gian xử lý đơn hàng  
- Tăng 25% tỷ lệ khách hàng quay lại nhờ hệ thống tích điểm  
- Cải thiện customer satisfaction score lên 90%  

*Kỹ năng phát triển*:  
- Thành thạo AWS Serverless Architecture  
- Kinh nghiệm phát triển full-stack với ReactJS và .NET  
- Hiểu biết sâu về NoSQL database design  
- Kỹ năng DevOps với CI/CD pipeline  

*Khả năng mở rộng*: Hệ thống có thể dễ dàng scale để phục vụ multiple coffee shops hoặc integrate thêm features như AI recommendation, loyalty program nâng cao.  
*Giá trị dài hạn*: Platform foundation có thể tái sử dụng cho các dự án e-commerce khác, tạo cơ sở cho việc phát triển các ứng dụng kinh doanh tương tự.
