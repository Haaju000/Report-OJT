---
title: "Deploy to AWS Amplify"
weight: 4
chapter: false
pre: " <b> 5.1.4 </b> "
---



In this step, we will connect the GitHub repository with AWS Amplify and deploy the application.

## 1. Access AWS Amplify Console

### 1.1 Login to AWS Console

1. Access AWS console home
2. Login with your AWS Account
3. Select region: **ap-southeast-1**

### 1.2 Open AWS Amplify

1. In the search bar, type "**Amplify**"
2. Click **AWS Amplify**


---

## 2. Create New App

### 2.1 Start with Amplify Hosting

1. Click **Get Started** in the **Amplify Hosting** section
2. Or click **Create New app**

![New App](/images/5-Workshop/create-new-app.png)

### 2.2 Authorize GitHub

1. Click **Authorize AWS Amplify**
2. Login to GitHub if prompted
3. Grant permissions to AWS Amplify

{{% notice info %}}
📝 **Note**: AWS Amplify needs repository access to pull code and setup webhooks
{{% /notice %}}

---

## 3. Add Repository

### 3.1 Select Repository

1. **Repository**: Select `Proposal-AWS---Coffe---FE`
2. **Branch**: Select `main`
3. Click **Next**

![Select GitHub](/images/5-Workshop/select-repo.png)

### 3.2 Configure Build Settings

AWS Amplify will automatically detect build settings for Vite project:

```yaml
version: 1
frontend:
  phases:
    preBuild:
      commands:
        - cd front        # if your React directory is /front
        - npm ci
    build:
      commands:
        - npm run build
  artifacts:
    baseDirectory: front/build
    files:
      - '**/*'
  cache:
    paths:
      - front/node_modules/**/*
```

#### Verify settings:
- ✅ **App name**: `coffee-cloud-frontend` (auto from repo name)
- ✅ **Environment name**: `main` (from branch name)
- ✅ **Build command**: `npm run build`
- ✅ **Build output directory**: `dist`

Click **Next**

---

## 4. Configure Advanced Settings (Optional)

### 4.1 Environment Variables

- `REACT_APP_API_URL`: Backend API deployment domain
- `REACT_APP_AWS_REGION`
- `REACT_APP_CLIENT_ID`
- `REACT_APP_USER_POOL_ID`
![Select GitHub](/images/5-Workshop/environment-amplify.png)

---

## 5. Monitor Deployment Process

AWS Amplify will start deployment with 4 phases:

### 5.1 Provision
⏳ **Duration**: ~30 seconds
- Allocate resources
- Setup build environment

### 5.2 Build
⏳ **Duration**: ~2-3 minutes
- Pull code from GitHub
- Run `npm ci` (install dependencies)
- Run `npm run build`
- Generate static files in `dist/`

### 5.3 Deploy
⏳ **Duration**: ~30 seconds
- Upload build artifacts to CloudFront CDN
- Configure SSL certificate
- Setup domain

### 5.4 Verify
⏳ **Duration**: ~10 seconds
- Health check
- Verify deployment success


---

## 6. Access Your App

### 6.1 Get URL

After successful deployment:
1. Amplify will display a URL like: `https://main.d3djm3hylbiyyu.amplifyapp.com/`
2. Click the URL to open the application

![App URL](/images/5-Workshop/domain-amplify.png)

### 6.2 Test Application

Verify all pages:
- ✅ Homepage (`/`)
- ✅ Menu page (`/menu`)
- ✅ Login page (`/login`)
- ✅ Navigation works

---


## 7. Auto-Deploy

Let's test the CI/CD pipeline:

1. Edit local files
2. Commit and push on GitHub Desktop:
3. Return to **Amplify Console** → You will see the build automatically trigger!
4. After ~3 minutes, refresh the app URL → See the changes!


---

## 8. View Build Logs

### 8.1 Access Logs

1. In Amplify Console, click on the **latest build**
2. Expand the phases to view logs:
   - **Provision logs**: Resource allocation
   - **Build logs**: npm install + build output
   - **Deploy logs**: Upload to CDN
   - **Verify logs**: Health checks
![App URL](/images/5-Workshop/log-amplify.png)
### 8.2 Download Logs

Click **Download build logs** to save logs to your machine

---


## Next Steps

Continue with [Testing](../5.1.5-testing/).
