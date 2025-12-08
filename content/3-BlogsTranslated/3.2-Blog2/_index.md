---
title: "Blog 2"
date: ""
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---


# The frugal HPC architect – ensuring effective FinOps for HPC workloads at scale

The article emphasizes that when using Amazon Web Services (AWS) to run HPC workloads, you need to treat cost as a “non-functional requirement” — balancing performance and cost to avoid waste.

To save money, they recommend measures such as: choosing the right instance, using EC2 Spot or Savings Plan, optimizing CPU/memory/storage usage, and closely monitoring performance & costs with observability tools.

---

## Background

- Amazon Web Services (AWS) article — “The frugal HPC architect – ensuring effective FinOps for HPC workloads at scale” analyzes how to apply Werner Vogels’ (The Frugal Architect) principles to high-performance workloads (HPC) running in the cloud.

- The goal is to help organizations using HPC in the cloud still ensure performance, scalability, flexibility — while controlling costs tightly and effectively.

# Key principles and practices

- Cost should be considered a “non-functional requirement” — alongside security, scalability, efficiency, etc. Cost should not be considered as the last consideration.

- Reduce “unit consumption”.

- With storage / I/O-intensive workloads: instead of keeping all data on a “fast storage” system, you can use a hybrid solution: for example, linking a high-performance storage system with object storage and loading data on demand, or using a cache, and only keeping the necessary data.

## Observe and measure

- According to the principle of “Unobserved systems lead to unknown costs”: If you do not monitor and measure clearly — you will not know the real costs and will not detect waste.

- Need a system of metrics + logs + tracing to measure: ratio of real compute / total capacity, cost compared to value created, analysis of usage, anomalies... AWS provides tools such as Amazon CloudWatch, AWS Compute Optimizer, usage/cost export reports, etc.

- Thanks to that, organizations can: identify excess, under-utilized resources; evaluate whether workloads are worth running; adjust configuration or infrastructure to save.

## Conclusion and Implications

- When moving HPC from on-premise to the cloud, cost is no longer a fixed price — it depends on how you design the architecture, use it, and manage it. “Frugal” needs to be considered as part of the design from the beginning.

- With the right approach: choosing the right instance, optimizing usage, using observability & FinOps tools — HPC in the cloud can be both powerful, flexible, and cost-effective. This helps organizations, businesses, or research institutes with high workloads (scientific simulation, AI/ML, big data processing, etc.) take advantage of the cloud without “breaking the budget”.

- The principles from The Frugal Architect — “cost as non-functional requirement”, “efficiency & effectiveness”, “observability” — are a mindset that should be applied not only to HPC but to all cloud-scale systems.
