---
title: "Publish .NET Application for Deployment"
weight: 2
chapter: false
pre: " <b> 5.2.2 </b> "
---



Before deploying to Elastic Beanstalk, we need to publish our .NET application into a deployment package.


#### Step 2: Publish to AWS on Visual Code Studio (Elastic Beanstalk)

![Select GitHub](/images/5-Workshop/publish-be.png)

This creates a `publish` folder with all necessary files.

#### Step 3: Auto create Zip file and deploy
![Select GitHub](/images/5-Workshop/auto-deploy.png)

Create a ZIP file from the published output

The second way is using this command to repushlish and rezip. Then upload that to Elastic Beanstalk Console:
```bash
dotnet publish -c Release -o ./publish
# Copy Procfile to publish folder
Copy-Item Procfile .\publish\
Compress-Archive -Path .\publish\* -DestinationPath CoffeeCloudAPI.zip -Force
```


#### Deployment Package Ready! 📦

You now have:
- ✅ `CoffeeShopAPI.zip` - Ready to upload to Elastic Beanstalk
- ✅ Swagger UI enabled for testing
- ✅ All dependencies included
- ✅ Proper configuration files

**File Location:**

![Select GitHub](/images/5-Workshop/publish-file.png)
#### Common Issues

**Issue:** ZIP file is too large (>512 MB)
**Solution:** 
- Remove unnecessary files from publish folder
- Check for duplicated dependencies
- Use `dotnet publish --self-contained false`

**Issue:** Swagger doesn't work after deployment
**Solution:**
- Make sure `UseSwagger()` is called without environment check
- Verify `appsettings.json` is included in ZIP
- Check HTTPS redirection settings

**Issue:** Application won't start
**Solution:**
- Verify `web.config` is present
- Check .NET version matches (8.0)
- Review CloudWatch logs after deployment

#### Next Steps

Now that we have our deployment package, let's upload it to AWS Elastic Beanstalk! →

