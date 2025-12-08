---
title: "Week 7 Worklog"
date: ""
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---


### Week 7 Objectives:

* Understand and deploy load distribution and automatic scaling systems using ALB/NLB, Target Group and Auto Scaling Group.
* Set up automatic scaling mechanisms (scheduled and dynamic) so that the system automatically increases/decreases the number of EC2s according to actual load.
* Complete ALB + ASG lab, including health check configuration and automatic scaling when CPU exceeds the threshold (>60%).

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2   | - Elastic Load Balancer (ALB, NLB)   <br>   - Create ALB                    | 09/20/2025 | 09/20/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 3   | - Target Group  <br>     - Health check                                     | 09/21/2025 | 09/21/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Auto Scaling Group (ASG)   <br>    - Launch Template                      | 09/22/2025 | 09/22/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Scaling Policies   <br>   - Scheduled & Dynamic Scaling                   | 09/23/2025 | 09/23/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - **Practice:** <br> + ALB + ASG <br> + Autoscale when CPU > 60%            | 09/24/2025 | 09/24/2025 | <https://cloudjourney.awsstudygroup.com/> |



### Week 7 Achievements:

* Successfully deployed ALB and ASG, enabling the system to distribute load and self-scale according to demand.

* Correctly configured Target Group and Health Check, ensuring only healthy EC2s are sent traffic.

* Set up and test Scaling Policies, allowing EC2 to automatically scale when CPU > 60% and operate stably under load conditions.