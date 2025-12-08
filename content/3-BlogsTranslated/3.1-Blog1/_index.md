---
title: "Blog 1"
date: ""
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---


# Getting Started with Healthcare Data Lakes: Using Microservices

The University of California, Irvine (UCI) used rclone in conjunction with Amazon Web Services (e.g., Amazon S3, IAM, CloudWatch, etc.) to establish a centralized backup system, protecting over 5 PB of research data (over 250 million files) from hundreds of servers in multiple labs.

This system allows for daily/incremental backups, while using long-term retention policies and monitoring tools to balance performance, security, and cost — providing a large-scale and efficient backup model for research environments.

---

## Background

- The University of California, Irvine (UCI) has thousands of individual research labs with data storage servers — a total of about 100 servers with about 10 PB of data to backup.

- Previously, individual backup solutions did not meet the requirements of cost, scale, and centralized management.

## UCI Solution

- UCI developed a centralized backup system using the open source tool rclone in collaboration with Amazon Web Services (AWS) services, including Amazon S3, Amazon S3 Glacier Deep Archive, AWS Identity and Access Management (IAM), Amazon CloudWatch, Amazon Simple Notification Service (SNS), and other automation services.

- Each research server is individually authorized and configured — with its own S3 bucket, its own IAM role, to ensure separation of administrative and security rights.

- The system performs daily incremental backups and weekly deep syncs, and uses lifecycle policies to move older data to long-term storage (Glacier Deep Archive), reducing long-term storage costs.

- The entire process — from job definition, cron scheduling, backup, security, monitoring, alerting, to recovery — is automated with Python code developed by UCI.

## Results

- The system has successfully backed up more than 5 PB of data, equivalent to more than 250 million files.

- UCI achieves a balance between performance, security, cost, and scalability: the system can handle servers from several TB to several PB, while still maintaining stable operations.

- This solution helps UCI have a clear roadmap, centralized management, and can be replicated to other units if needed.

## Implications and Suggestions

- For research organizations or enterprises with large data volumes, UCI's approach — combining rclone + AWS + automation — is an effective reference pattern for backing up data at petabyte scale.

- Separating administration (sysadmin) and cloud management (cloudadmin) enhances security and reduces the risk of errors.

- Incremental backup + lifecycle storage optimizes long-term storage costs — suitable for research data or long-term storage.
