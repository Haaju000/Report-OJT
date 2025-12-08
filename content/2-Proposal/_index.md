---
title: "Proposal"
weight: 2
chapter: false
pre: " <b> 2. </b> "
---


# Coffee Cloud – Coffee Shop Order Platform
---

### Project Documentation

📄 **[Download Complete Project Proposal (Word Document)](/documents/Coffee-Cloud-Complete-Proposal.docx)**

---
### 1. Executive Summary
The "Coffee Cloud – Coffee Shop Order Platform" project is a web platform that helps customers order coffee online, accumulate points after each order, and redeem promotional vouchers.

The system supports three user groups: Customer, Shipper, and Admin, aiming to optimize the ordering experience, delivery, and operational management of the coffee shop.

The frontend application is built with ReactJS, backend with C#/.NET running on AWS Lambda, connected via API Gateway and deployed entirely on AWS Free Tier with services: Amplify (Hosting + CI/CD), Cognito (Authentication), Lambda .NET (Backend logic), S3 Storage, DynamoDB, SNS (Notifications), SES (Email Service), IAM, and CloudWatch Logs.

### 2. Problem Statement
### What's the Problem?
Traditional coffee shops face difficulties managing crowded orders, customers have to wait long to place orders and receive products. There is no point accumulation system to encourage customers to return, and order status tracking is not transparent.

### The Solution
The Coffee Cloud platform is built with scalable cloud architecture on AWS, using ReactJS for frontend hosted on Amplify, and containerized backend services deployed on Elastic Beanstalk. The system provides three separate interfaces for Customer (ordering, point accumulation), Shipper (receiving and delivering), and Admin (overall management). Data is stored in DynamoDB for high performance with S3 for static assets and Amazon Location Service for delivery tracking. Authentication is managed by Cognito with multi-role support. AWS SNS handles real-time notifications about order status, while SES manages email communications. Payment processing is integrated through external payment gateways. Key features include online ordering, point system, real-time order tracking with GPS, inventory management, and multi-channel notification system.

### Benefits and Return on Investment
The system helps increase revenue through online channels, reduces customer waiting time, and optimizes operational processes. Low deployment cost thanks to AWS Free Tier usage, estimated monthly operating cost under $5 USD for the initial phase. The point system helps increase customer return rate, expected to increase revenue by 20-30% compared to traditional methods. Return on investment time is estimated at 3-6 months thanks to saving labor costs and increasing sales efficiency.

### 3. Solution Architecture
Coffee Cloud adopts a scalable containerized architecture on AWS to ensure high availability and cost efficiency. The ReactJS frontend is deployed on AWS Amplify with automatic CI/CD integration from Git repository. Backend services are containerized and deployed on AWS Elastic Beanstalk for easy scaling and management. Data is stored in DynamoDB for high performance, S3 for static assets, and Amazon Location Service for GPS tracking and delivery optimization. Authentication and authorization are managed by Amazon Cognito with multi-role support (Customer, Shipper, Admin). External payment services are integrated for secure transaction processing.

![Coffee Cloud Platform Architecture](/images/2-Proposal/architecture_proposal.jpg)

### AWS Services Used
- **AWS Amplify**: Hosts ReactJS frontend with automatic CI/CD pipeline from Git repository.
- **AWS Elastic Beanstalk**: Containerized .NET Framework 8.0 backend services with auto-scaling and load balancing.
- **Amazon DynamoDB**: NoSQL database storing users, orders, products, points data.
- **Amazon S3**: Stores static assets like product images, documents, and backup data.
- **Amazon Location Service**: GPS tracking, geocoding, and route optimization for delivery.
- **Amazon Cognito**: Authentication and authorization for 3 user role types.
- **Amazon SNS**: Push notifications and SMS alerts for order status and promotions.
- **Amazon SES**: Email service for order confirmations, receipts, and marketing campaigns.
- **Cloudflare Tunnel**: Secure domain connection between Amplify frontend and Elastic Beanstalk backend using Quick Tunnel.
- **Payment Gateway Integration**: External payment processing for secure transactions.
- **Amazon CloudWatch**: Monitoring and logging for the entire system.
- **AWS IAM**: Manages permissions and security policies.

### Component Design
- **Frontend Layer**: ReactJS application hosted on Amplify with responsive design and Git-based CI/CD.
- **Application Layer**: Containerized .NET Framework 8.0 services deployed on Elastic Beanstalk with auto-scaling capabilities.
- **Network Layer**: Cloudflare Tunnel (Quick Tunnel) providing secure domain connection between frontend and backend services.
- **Data Storage Layer**: DynamoDB for structured data, S3 for file storage, Location Service for GPS data.
- **Authentication Layer**: Cognito User Pools manage users with 3 groups (Customer, Shipper, Admin).
- **Communication Layer**: SNS for real-time notifications, SES for email communications.
- **Payment Layer**: Integrated external payment gateways for secure transaction processing.
- **Monitoring Layer**: CloudWatch tracks performance, errors, and usage metrics with IAM security controls.

### 4. Technical Implementation
**Implementation Phases**
The Coffee Cloud project is divided into 4 main phases over 3 months:
1. **Research and Design**: Analyze business requirements, design database schema, wireframe UI/UX and system architecture (Month 1).
2. **Environment Setup and Backend Development**: Configure AWS services, develop containerized backend services, set up DynamoDB tables and Elastic Beanstalk environment (Month 1-2).
3. **Frontend Development**: Build ReactJS application, integrate with backend APIs, implement authentication flow with Cognito (Month 2).
4. **Testing and Deployment**: Unit testing, integration testing, performance testing, deploy to Amplify and Elastic Beanstalk with monitoring (Month 3).

**Technical Requirements**
- **Frontend Requirements**: ReactJS with hooks, React Router for navigation, Axios for API calls, CSS frameworks (Bootstrap/Material-UI), responsive design for mobile and desktop.
- **Backend Requirements**: Containerized .NET Framework 8.0 services on Elastic Beanstalk, Entity Framework Core for data access, JWT authentication, exception handling and logging.
- **Database Design**: DynamoDB tables for Users, Products, Orders, OrderItems, Points, Vouchers with proper indexing and relationships.
- **Location Services**: Amazon Location Service integration for GPS tracking, geocoding, and route optimization.
- **Payment Integration**: External payment gateway APIs for secure transaction processing.
- **Network Integration**: Cloudflare Tunnel (Quick Tunnel) for secure connection between Amplify frontend and Elastic Beanstalk backend.
- **DevOps Requirements**: Git version control, Amplify CI/CD pipeline, Elastic Beanstalk deployment, CloudWatch monitoring, IAM roles and policies for security.

### 5. Timeline & Milestones
**Project Timeline**
- **Phase 1 (Week 1-4)**: System Research and Design
    - Analyze business and technical requirements
    - Design database schema and API specifications
    - Create wireframes and UI mockups
    - Setup AWS account and initial configuration
- **Phase 2 (Week 5-8)**: Backend and Infrastructure Development
    - Create DynamoDB tables and configure indexes
    - Develop containerized backend services with C#/.NET
    - Setup Elastic Beanstalk environment and deployment
    - Configure Cognito User Pools and Groups
    - Integrate Amazon Location Service for GPS tracking
    - Setup payment gateway integration
- **Phase 3 (Week 9-10)**: Frontend Development
    - Build ReactJS components and pages
    - Implement authentication and authorization
    - Integrate with backend APIs
    - Responsive design for mobile
- **Phase 4 (Week 11-12)**: Testing and Deployment
    - Unit testing and integration testing
    - Deploy to AWS Amplify
    - Performance optimization and monitoring setup
    - User acceptance testing and documentation

### 6. Budget Estimation
The Coffee Cloud project is designed to maximize AWS Free Tier usage during the initial development and testing phase.

### Infrastructure Costs
**AWS Services (Monthly)**
- AWS Amplify: $0.00 USD (Free Tier: 1000 build minutes, 15GB storage)
- AWS Elastic Beanstalk: $0.00 USD (Free Tier: t3.micro instance, 750 hours/month)
- Amazon DynamoDB: $0.00 USD (Free Tier: 25GB storage, 25 RCU/WCU)
- Amazon S3: $0.00 USD (Free Tier: 5GB standard storage)
- Amazon Location Service: $0.00 USD (Free Tier: 5000 requests/month)
- Amazon Cognito: $0.00 USD (Free Tier: 50,000 MAU)
- Amazon SNS: $0.00 USD (Free Tier: 1M publications, 100,000 HTTP/HTTPS requests)
- Amazon SES: $0.00 USD (Free Tier: 62,000 emails/month)
- Amazon CloudWatch: $0.00 USD (Free Tier: 10 custom metrics, 5GB logs)

**Post Free Tier Costs (Estimated for production)**
- AWS Amplify: ~$1.00 USD/month (hosting + build minutes)
- AWS Elastic Beanstalk: ~$15.00 USD/month (t3.small instance for production)
- Amazon DynamoDB: ~$1.25 USD/month (additional RCU/WCU)
- Amazon Location Service: ~$2.00 USD/month (additional GPS requests)
- Amazon SNS: ~$0.50 USD/month (additional notifications + SMS)
- Amazon SES: ~$1.00 USD/month (additional emails beyond free tier)
- Payment Gateway Fees: ~$5.00 USD/month (transaction processing fees)

**Total Estimation**: $0.00 USD/month (Development), ~$25.75 USD/month (Production)
**Development Cost**: Only incurs developer labor costs

### 7. Risk Assessment
#### Risk Matrix
- Exceeding Free Tier limits: Medium impact, medium probability
- Integration errors between AWS services: High impact, low probability
- DynamoDB performance issues: Medium impact, low probability
- Security vulnerabilities: High impact, low probability

#### Mitigation Strategies
- Cost: Set up CloudWatch billing alerts, monitor usage daily
- Integration: Perform thorough testing, use AWS SAM for local testing
- Performance: Design proper DynamoDB indexes, implement caching strategies
- Security: Follow AWS security best practices, regular security audits

#### Contingency Plans
- Backup and recovery plan for DynamoDB data
- Fallback mechanisms for critical functions
- Manual operation procedures if system fails
- Communication plan with stakeholders during incidents

### 8. Expected Outcomes
#### Technical Improvements
Complete Coffee Cloud system capable of handling hundreds of concurrent orders, responsive design working smoothly on all devices.

#### Business Benefits
- 30% revenue increase through new online channel
- 50% reduction in order processing time
- 25% increase in customer return rate through point system
- Improve customer satisfaction score to 90%

#### Skill Development
- Master AWS Serverless Architecture
- Full-stack development experience with ReactJS and .NET
- Deep understanding of NoSQL database design
- DevOps skills with CI/CD pipeline

#### Scalability
The system can easily scale to serve multiple coffee shops or integrate additional features like AI recommendations, advanced loyalty programs.

#### Long-term Value
Platform foundation can be reused for other e-commerce projects, creating a foundation for developing similar business applications.
