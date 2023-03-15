---
description: Layer 4
---

# Network Load Balancer (v2)

* Network load balancers (Layer 4) allow to:&#x20;
  * Forward TCP & UDP traffic to your instances&#x20;
  * Handle millions of request per seconds&#x20;
  * Less latency \~100 ms (vs 400 ms for ALB
* <mark style="color:green;">**NLB has one static IP per AZ, and supports assigning Elastic IP**</mark> (helpful for whitelisting specific IP)
* NLB has one static IP per AZ, and supports assigning Elastic IP (helpful for whitelisting specific IP)
* <mark style="color:orange;">Not included in the AWS free tier</mark>

## Target Groups for NLB

* EC2 instances&#x20;
* IP Addresses – must be private IPs&#x20;
* Application Load Balancer&#x20;
* Health Checks support the TCP, HTTP and HTTPS Protocols

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

