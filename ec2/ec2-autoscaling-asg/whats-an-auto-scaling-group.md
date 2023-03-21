---
description: Scale for your users, make yourself available.
---

# What’s an Auto Scaling Group?

* In real-life, the load on your websites and application can change.&#x20;
* In the cloud, you can create and get rid of servers very quickly.&#x20;
* The goal of an Auto Scaling Group (ASG) is to:&#x20;
  * Scale out (add EC2 instances) to match an increased load.&#x20;
  * Scale in (remove EC2 instances) to match a decreased load.&#x20;
  * Ensure we have a minimum and a maximum number of EC2 instances running.&#x20;
  * Automatically register new instances to a load balancer&#x20;
  * Re-create an EC2 instance in case a previous one is terminated (ex: if unhealthy)
* ASG are free (you only pay for the underlying EC2 instances)

## Auto Scaling Group Attributes

* A Launch Template (older “Launch Configurations” are deprecated)&#x20;
  * AMI + Instance Type&#x20;
  * EC2 User Data&#x20;
  * EBS Volumes&#x20;
  * Security Groups&#x20;
  * SSH Key Pair&#x20;
  * IAM Roles for your EC2 Instances&#x20;
  * Network + Subnets Information&#x20;
  * Load Balancer Information&#x20;
* Min Size / Max Size / Initial Capacity&#x20;
* Scaling Policies

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

## CloudWatch Alarms & Scaling

* It is possible to scale an ASG based on CloudWatch alarms.&#x20;
* An alarm monitors a metric (such as Average CPU, or a custom metric)&#x20;
* Metrics such as Average CPU are computed for the overall ASG instances.&#x20;
* Based on the alarm:&#x20;
  * We can create scale-out policies (increase the number of instances)&#x20;
  * We can create scale-in policies (decrease the number of instances)

## Auto Scaling Groups – Dynamic Scaling Policies

* **Target Tracking Scaling**&#x20;
  * Most simple and easy to set-up&#x20;
  * Example: I want the average ASG CPU to stay at around 40%&#x20;
* **Simple / Step Scaling**&#x20;
  * When a CloudWatch alarm is triggered (example CPU > 70%), then add 2 units&#x20;
  * When a CloudWatch alarm is triggered (example CPU < 30%), then remove 1&#x20;
* **Scheduled Actions**&#x20;
  * Anticipate a scaling based on known usage patterns&#x20;
  * Example: increase the min capacity to 10 at 5 pm on Fridays
* **Predictive scaling:**&#x20;
  * continuously forecast load and schedule scaling ahead

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption><p>Predictive Scaling</p></figcaption></figure>

## Good metrics to scale on

* **CPUUtilization**: Average CPU utilization across your instances&#x20;
* **RequestCountPerTarget**: to make sure the number of requests per EC2 instances is stable&#x20;
* **Average Network In / Out** (if you’re application is network bound)&#x20;
* **Any custom metric** (that you push using CloudWatch)

## Auto Scaling Groups - Scaling Cooldowns

* After a scaling activity happens, <mark style="color:yellow;">**you are in the cooldown period (default 300 seconds)**</mark>&#x20;
* During the cooldown period, the ASG will not launch or terminate additional instances (to allow for metrics to stabilize)&#x20;
* Advice: Use a ready-to-use AMI to reduce configuration time in order to be serving request fasters and reduce the cooldown period

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>
