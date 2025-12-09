---
title: "Testing & Verification"
weight: 5
chapter: false
pre: " <b> 5.1.5 </b> "
---



## 1. Functional Testing

### 1.1 Test all pages

-  Homepage loads correctly
-  Menu displays products
-  Login form displays
-  Navigation works
-  Footer displays

### 1.2 Test Routing

Test the URLs:
```
https://main.d3djm3hylbiyyu.amplifyapp.com/
https://main.d3djm3hylbiyyu.amplifyapp.com/menu
https://main.d3djm3hylbiyyu.amplifyapp.com/login
```

Refresh each page → No 404 error ✅

## 4. CI/CD Testing

### 4.1 Test Auto-Deploy

1. Make code changes
2. Commit and push on GitHub Desktop
3. Verify auto-deploy triggers
4. Check deploy success

## 5. Cleanup (Optional)

If you want to delete the app to avoid costs:

1. Amplify Console → **Actions** → **Delete app**
2. Confirm deletion


