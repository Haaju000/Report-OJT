---
title: "Testing API with Swagger UI"
weight: 4
chapter: false
pre: " <b> 5.2.4 </b> "
---



Now let's test your deployed API using Swagger UI and connect it to your Amplify frontend.

#### Step 1: Access Swagger UI

Open your browser and navigate to:
```
http://fixenv-env.eba-vgperhwx.ap-southeast-1.elasticbeanstalk.com/swagger
```

Replace with your actual Elastic Beanstalk domain.

You should see the **Swagger UI** interface with all your API endpoints listed.

#### Step 8: Connect to Amplify Frontend with Cloudflare Tunnel

Since Elastic Beanstalk gives you HTTP (not HTTPS), and Amplify requires HTTPS, we'll use **Cloudflare Tunnel** (Quick Tunnel).

**Why Cloudflare Tunnel?**
- ✅ Converts HTTP to HTTPS
- ✅ Free and easy to use
- ✅ No SSL certificate needed
- ✅ Works with Amplify CORS

**Install Cloudflare Tunnel:**

**Windows:**
```powershell
PS C:\Users\hp> cd C:\Users\hp\Documents\GitHub\Coffe-shop-oder-platfrom
PS C:\Users\hp\Documents\GitHub\Coffe-shop-oder-platfrom> .\quick-tunnel.ps1 
```

#### Step 9: Run Quick Tunnel

**Output will show:**
![Select GitHub](/images/5-Workshop/eb-cloudflare.png)

**Important:** Copy this HTTPS URL! This is your secure tunnel endpoint.

**Keep this terminal running!** The tunnel only works while the command is active.

#### Step 11: Update Amplify Frontend Environment Configuration

In your React frontend code, update the API base URL:

![Select GitHub](/images/5-Workshop/environment-amplify.png)



#### Step 12: Test Frontend Connection

1. **Deploy updated frontend to Amplify**
   ```bash
   git add .
   git commit -m "Add backend API integration"
   git push origin main
   ```

2. **Wait for Amplify build** (2-3 minutes)

3. **Test on Amplify domain:**
   - Visit your Amplify app
   - Open browser DevTools (F12)
   - Go to Network tab
   - Interact with menu/order features
   - Should see API calls to Cloudflare tunnel URL
   - Check for successful responses (200, 201)

#### Step 13: Verify CORS

If you see CORS errors in console:

1. **Update backend CORS settings**
```
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
2. Redeploy to Elastic Beanstalk
![Select GitHub](/images/5-Workshop/publish-be.png)
3. Restart Cloudflare tunnel
4. Test again

**Check in DevTools Console:**
```
✅ Good: Response received successfully
❌ Bad: CORS policy blocked the request
```

#### Monitoring and Debugging

**Check Logs:**
1. Go to Elastic Beanstalk Console
2. Environment → Logs → Request Logs
3. Click "Last 100 Lines"
4. Review for errors

**CloudWatch Logs:**
1. CloudWatch Console
2. Log Groups → `/aws/elasticbeanstalk/your-env`
3. View detailed application logs


