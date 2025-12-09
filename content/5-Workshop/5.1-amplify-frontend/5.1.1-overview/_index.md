---
title: "Workshop Overview"
weight: 1
chapter: false
pre: " <b> 5.1.1 </b> "
---



#### Workshop Objectives

After completing this workshop, you will be able to:
- ✅ Create a ReactJS application from scratch
- ✅ Setup Git repository and push code to GitHub
- ✅ Connect GitHub repository with AWS Amplify
- ✅ Deploy application with automatic CI/CD
- ✅ Access application via HTTPS URL
- ✅ Understand the build process and environment variables

#### Coffee Cloud Frontend - Basic Features

In this workshop, we will create a basic interface for Coffee Cloud Platform including:
- 🏠 **Homepage**: Introduction to Coffee Cloud
- 📋 **Menu Page**: Coffee product list
- 👤 **Login Page**: Login page (will integrate Cognito in Workshop 2)

#### Technologies Used

- **Frontend Framework**: ReactJS 
- **Build Tool**: Create React App
- **Version Control**: Git + GitHub
- **Hosting**: AWS Amplify
- **CDN**: CloudFront (automatic from Amplify)

#### Deployment Architecture

```
┌─────────────────┐
│  Developer      │
│  (Your Laptop)  │
└────────┬────────┘
         │ git push
         ▼
┌─────────────────┐
│  GitHub         │
│  Repository     │
└────────┬────────┘
         │ webhook trigger
         ▼
┌─────────────────┐
│  AWS Amplify    │
│  - Build        │
│  - Deploy       │
└────────┬────────┘
         │ distribute
         ▼
┌─────────────────┐
│  CloudFront CDN │
│  (Global)       │
└────────┬────────┘
         │ HTTPS
         ▼
┌─────────────────┐
│  End Users      │
└─────────────────┘
```

#### Automatic CI/CD Process

1. Developer pushes code to GitHub
2. GitHub webhook triggers AWS Amplify build
3. Amplify automatically:
   - Pulls code from GitHub
   - Runs `npm install`
   - Runs `npm run build`
   - Deploys build artifacts to CloudFront CDN
4. Website automatically updates (2-3 minutes)

#### Estimated Costs

With **AWS Free Tier**, this workshop is **completely free**:
- ✅ 1000 build minutes/month (Free Tier)
- ✅ 15GB storage (Free Tier)
- ✅ 15GB data transfer out (Free Tier)

After Free Tier expires:
- Build: ~$0.01/minute
- Hosting: ~$0.15/GB stored/month
- Data transfer: ~$0.15/GB served

**Estimated cost**: Less than $1/month for small traffic


{{% notice tip %}}
💡 **Tip:** It's recommended to create a Git repository before starting to code so you can commit frequently
{{% /notice %}}

#### Next Steps

Start with [Prerequisites](../5.1.2-prerequisites/) to prepare your working environment.
