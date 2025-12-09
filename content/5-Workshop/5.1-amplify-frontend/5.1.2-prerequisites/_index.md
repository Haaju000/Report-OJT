---
title: "Prerequisites"
weight: 2
chapter: false
pre: " <b> 5.1.2 </b> "
---



Before starting the workshop, ensure you have prepared the following requirements:

## 1. AWS Account

### 1.1 Setup Billing Alerts

1. Login to **AWS Console**: [https://console.aws.amazon.com](https://console.aws.amazon.com)
2. Click on account name (top right) → **Billing Dashboard**
3. In sidebar, select **Billing Preferences**
4. Enable:
   - **Receive Free Tier Usage Alerts**
   - **Receive Billing Alerts**
5. Click **Save preferences**

### 1.2 Create CloudWatch Billing Alarm

1. In **Billing Dashboard**, click **Budgets** (sidebar)
2. Click **Create budget**
3. Select **Cost budget - Recommended**
4. Configure:
   - Budget name
   - Budgeted amount
   - Budget scope: All AWS services
5. Click **Create budget**

---

## 2. AWS CLI (Optional - Recommended)

### 2.1 Install AWS CLI

#### Windows:
```bash
msiexec.exe /i https://awscli.amazonaws.com/AWSCLIV2.msi
```

### 2.2 Configure AWS CLI

```bash
aws configure
```

Enter:
- AWS Access Key ID: (Secret Key)
- AWS Secret Access Key: (Secret Key)
- Default region: `ap-southeast-1`
- Default output format: `json`

---

## Next Steps

Continue with [Setup Github Repository](../5.1.3-setup-git/) to create the Coffee Cloud application.
