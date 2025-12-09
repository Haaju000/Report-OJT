---
title: "Workshop Overview"
weight: 1
chapter: false
pre: " <b> 5.2.1 </b> "
---



#### What You'll Build

In this workshop, you'll create a production-ready **.NET 8.0 Web API** backend for **Coffee Cloud Platform** and deploy it directly to **AWS Elastic Beanstalk** via AWS Console. The API includes **Swagger UI** for easy testing and documentation.

- ☕ **Menu Management** - Get all products, filter by category
- 🛒 **Order Processing** - Create orders, update status, track orders
- 👤 **User Management** - Customer, Shipper, Admin roles
- 📊 **Analytics** - Order statistics, revenue reports
- 📝 **Swagger UI** - Interactive API documentation and testing

#### Architecture Overview

```
┌─────────────────────────────────────────────────────┐
│           ReactJS Frontend (Amplify)                │
│   https://main.d3djm3hylbiyyu.amplifyapp.com/       │
└──────────────────┬──────────────────────────────────┘
                   │ HTTPS API Calls
                   ▼
┌─────────────────────────────────────────────────────┐
│      Application Load Balancer (ALB)                │
│         - Health checks                             │
│         - SSL termination                           │
└──────────────────┬──────────────────────────────────┘
                   │
        ┌──────────┴──────────┐
        ▼                     ▼
┌──────────────┐      ┌──────────────┐
│ EC2 Instance │      │ EC2 Instance │
│   (t3.micro) │      │   (t3.micro) │
│              │      │              │
│  .NET 8.0    │      │  .NET 8.0    │
│  Web API     │      │  Web API     │
│              │      │              │
│  + Swagger   │      │  + Swagger   │
└──────┬───────┘      └──────┬───────┘
       │                     │
       └──────────┬──────────┘
                  ▼
          ┌───────────────┐
          │   DynamoDB    │
          │               │
          │ - MenuItems   │
          │ - Orders      │
          │ - Users       │
          └───────────────┘
```

#### Key Technologies

| Technology | Purpose | Why? |
|------------|---------|------|
| **.NET 8.0** | Web API Framework | Modern, fast, cross-platform C# |
| **Swagger UI** | API Documentation | Interactive testing, auto-generated docs |
| **Elastic Beanstalk** | Platform Service | Auto-scaling, load balancing, monitoring |
| **DynamoDB** | NoSQL Database | Serverless, scalable, low latency |
| **CloudWatch** | Monitoring | Logs, metrics, alarms |


#### Cost Estimation

**Free Tier Eligible:**
- Elastic Beanstalk: No additional charge
- EC2 t3.micro: 750 hours/month (1 instance = free)
- DynamoDB: 25 GB storage, 25 WCU/RCU
- Data Transfer: 15 GB/month outbound

**After Free Tier:**
- 2 x t3.micro instances: ~$16/month
- Application Load Balancer: ~$16/month
- DynamoDB: Pay per use (~$1-5/month for small apps)



