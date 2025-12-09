---
title: "Deploy to AWS Elastic Beanstalk"
weight: 3
chapter: false
pre: " <b> 5.2.3 </b> "
---



Now let's deploy your .NET API to Elastic Beanstalk using AWS Console.

#### Step 1: Access Elastic Beanstalk Console

1. Login to [AWS Console](https://console.aws.amazon.com/)
2. Search for **"Elastic Beanstalk"** in the top search bar
3. Click **Elastic Beanstalk** service

#### Step 2: Create New Application

1. Click **"Create Application"** button
2. Fill in application details

#### Step 3: Configure Environment

**Environment information:**
![Select GitHub](/images/5-Workshop/env-eb.png)

**Platform:**
- **Platform:** `.NET on Windows Server`
- **Platform branch:** `.NET 8 running on 64bit Windows Server 2022`
- **Platform version:** Latest (Recommended)

#### Step 4: Upload Application Code

**Application code:**
- Select **"Upload your code"**
- **Version label:** `v1.0.0` (or current date like `2025-12-08`)
- **Source code origin:** Choose file
- Click **"Choose file"** and select your `publish.zip`

⚠️ **Important:** Make sure you're uploading the ZIP file, not the folder!

#### Step 5: Configure Service Access

**Service role:**
- If first time: Click **"Create and use new service role"**
- Role name: `aws-elasticbeanstalk-service-role` (auto-generated)

**EC2 key pair (optional):**
- Select existing or skip (not needed for basic deployment)

**EC2 instance profile:**
- If first time: Click **"Create new instance profile"**
- Use: `aws-elasticbeanstalk-ec2-role`

#### Step 6: Set up Networking (Optional)

**Virtual Private Cloud (VPC):**
- Use default VPC (recommended for testing)

**Public IP address:**
- ✅ Activate (required for internet access)

Skip other networking options for now.

#### Step 7: Configure Instance

**Instance types:**
- Select: `t3.micro` (Free Tier eligible!)
- Remove other instance types

**Root volume:**
- Type: `General Purpose (SSD)`
- Size: `10 GB` (default)

#### Step 8: Configure Auto-Scaling

**Environment type:**

**For Single Instance (Free Tier):**
- Just 1 instance, no scaling
- Good for testing/development

#### Step 9: Configure Health Monitoring

**Health reporting:**
- System: `Enhanced` (recommended)
![Select GitHub](/images/5-Workshop/health-eb.png)


#### Step 10: Configure Environment Properties

Scroll to **Environment properties** section and add:

![Select GitHub](/images/5-Workshop/env-eb.png)

#### Step 11: Review and Create

1. Review all settings
2. Click **"Submit"**
3. Wait for environment creation (5-10 minutes)

You'll see:
- 🔄 **Creating environment** (yellow)
- 🔄 **Launching instances**
- 🔄 **Running deployment**
- ✅ **Environment created successfully** (green)

#### Step 12: Get Your API URL

Once deployment is complete:

1. You'll see your domain at the top:
   ```
   http://fixenv-env.eba-vgperhwx.ap-southeast-1.elasticbeanstalk.com/
   ```

2. **Test Swagger UI:**
   ```
   http://fixenv-env.eba-vgperhwx.ap-southeast-1.elasticbeanstalk.com/swagger
   ```


#### Step 14: Configure CORS for Amplify


Update `Program.cs` and redeploy:
```csharp
builder.Services.AddCors(options =>
{
    options.AddPolicy("AllowAll", policy =>
    {
        policy.WithOrigins("http://localhost:3000",
                "https://main.d3djm3hylbiyyu.amplifyapp.com",
               "http://fixenv-env.eba-vgperhwx.ap-southeast-1.elasticbeanstalk.com")
              .AllowAnyMethod()
              .AllowAnyHeader()
  .AllowCredentials();
    });
});
```

#### Common Issues & Solutions

**Issue: Environment health is red/degraded**
- Check CloudWatch Logs: Configuration → Software → View logs
- Verify .NET 8.0 SDK version
- Check if `web.config` is in ZIP

**Issue: 502 Bad Gateway**
- Application failed to start
- Check logs for .NET errors
- Verify all dependencies are included

**Issue: Cannot access /swagger**
- Check if Swagger is enabled in production
- Verify app is running on correct port (5000)
- Check security group allows HTTP traffic

**Issue: CORS errors from frontend**
- Update CORS policy in `Program.cs`
- Add Amplify domain to allowed origins
- Redeploy with updated settings

#### Monitoring Your Application

**CloudWatch Logs:**
1. Configuration → Software
2. Click **"CloudWatch logs"**
3. View application logs and errors

**Metrics:**
1. Monitoring tab
2. View CPU, Memory, Network usage
3. Set up alarms for high usage

**Health:**
1. Main dashboard shows health status
2. Green = Healthy
3. Yellow = Warning
4. Red = Degraded/Severe

#### Cost Optimization

**Free Tier Usage:**
- 1 t2.micro instance: FREE
- Load Balancer: ~$16/month
- Data transfer: 15GB free/month

**To Stay in Free Tier:**
- Use **Single instance** environment type
- Keep 1 t2.micro instance
- Monitor data transfer

**To Scale Up (When Ready):**
- Switch to Load Balanced
- Increase min/max instances
- Enable auto-scaling

**Next:** Let's test all the API endpoints with Swagger! →

