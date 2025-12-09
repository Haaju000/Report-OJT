---
title: "Deploy ReactJS Frontend with AWS Amplify"
weight: 1
chapter: false
pre: " <b> 5.1 </b> "
---



#### Overview

In this workshop, you will learn how to deploy a ReactJS application for Coffee Cloud Platform to **AWS Amplify** with automatic CI/CD capabilities. AWS Amplify makes it easy to host static websites and automatically build + deploy every time you push code to your Git repository.

**AWS Amplify** is a fully-managed service that helps deploy and host frontend web applications with the following features:
- 🚀 Automatic CI/CD pipeline from Git repository
- 🔒 Built-in free SSL certificate
- 🌍 Global CDN with high performance
- 💰 Free tier: 1000 build minutes/month, 15GB storage

#### Architecture

```
GitHub Repository → AWS Amplify → CloudFront CDN → Users
     ↓ (push code)      ↓ (auto build)    ↓ (distribute)
```

#### Contents

1. [Workshop Overview](5.1.1-overview/)
2. [Prerequisites](5.1.2-prerequisites/)
3. [Setup Git Repository](5.1.3-setup-git/)
4. [Deploy to AWS Amplify](5.1.4-deploy-amplify/)
5. [Testing & Verification](5.1.5-testing/)

#### Completion Time
⏱️ Approximately **60-90 minutes**

#### Requirements
- ✅ AWS Account (Free Tier eligible)
- ✅ GitHub account
- ✅ Node.js 18+ and npm
- ✅ Git installed
- ✅ Code editor (VS Code recommended)
