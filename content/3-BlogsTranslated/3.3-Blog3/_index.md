---
title: "Blog 3"
date: ""
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---


# Enhance API throttling visibility with Amazon QuickSight

This article shows you how to use Amazon QuickSight to create a centralized dashboard that aggregates and displays fragmented data about API throttling from multiple accounts and regions of Amazon Web Services.

This allows you to easily track which APIs are throttled, in which accounts/regions, and assess the impact, adjust the frequency of API calls, and improve the retry logic to optimize operations.

---

## Background

- The Amazon Web Services (AWS) Amazon QuickSight (QuickSight) article, titled Enhance API throttling visibility with Amazon QuickSight, discusses using QuickSight to help organizations with multiple AWS accounts and multiple regions centrally monitor and display API throttling information.

- “Throttling” here means when AWS APIs exceed a rate limit — causing errors, which can lead to retries, system disruptions, or additional costs if left unchecked.

## Solution and architecture

- The solution uses a hub-and-spoke model: a “data-collection” account acts as a hub to collect data from multiple other AWS accounts (spokes) in multiple Regions.

- When an API is throttled in any account, the event is recorded by AWS CloudTrail (with an errorCode like Client.RequestLimitExceeded or ThrottlingException) → sent to Amazon EventBridge → filtered out the throttling event → sent to a custom event bus in the data-collection account.

- Then, these events are passed through Amazon Kinesis Data Firehose → saved to Amazon S3 → cataloged by AWS Glue → then used to query using Amazon Athena → the data is used by QuickSight to display on the dashboard.

- The QuickSight dashboard aggregates information: which APIs are throttled, which AWS services, which accounts/Regions, which IAM users/roles — giving you a clear “big picture” of throttling across the entire organization.

## Benefits and When to Use

- Allows centralized monitoring — instead of having to check each account/region individually, you have a common dashboard.

- Helps assess the overall throttling impact: know which APIs, which regions are throttled a lot, from there adjust rates, retry logic, or redesign workflows to avoid waste or errors.

- Especially useful for large organizations, multiple AWS accounts or multiple regions, multiple services — where manual monitoring is nearly impossible.

- Helps improve reliability, reduce errors due to throttling, control costs and optimize API performance.

# Some things to note and requirements

- Requires QuickSight Enterprise Edition + enough SPICE capacity to store and process data.

- Must have AWS CloudFormation / StackSets deployment rights to deploy resources (EventBridge, Firehose, S3, Glue, etc.) across accounts/regions.

- Currently the solution only applies to CloudTrail management API calls, as CloudTrail “data events” do not support sending to EventBridge at the time of writing.
