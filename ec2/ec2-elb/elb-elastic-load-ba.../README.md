---
description: distribute the load.
---

# ELB - Elastic Load Ba...

* An Elastic Load Balancer is a managed load balancer.&#x20;
  * [x] AWS guarantees that it will be working.&#x20;
  * [x] AWS takes care of upgrades, maintenance, high availability.&#x20;
  * [x] AWS provides only a few configuration knobs.&#x20;
* It costs less to setup your own load balancer, but it will be a lot more effort on your end.&#x20;
* It is integrated with many AWS offerings / services.&#x20;
  * EC2, EC2 Auto Scaling Groups, Amazon ECS.&#x20;
  * AWS Certificate Manager (ACM), CloudWatch.&#x20;
  * Route 53, AWS WAF, AWS Global Accelerator.

## Types of load balancer on AWS

* AWS has 4 kinds of managed Load Balancers&#x20;
* <mark style="color:yellow;">**Classic Load Balancer (v1 - old generation) – 2009 – CLB**</mark> <mark style="color:yellow;"></mark><mark style="color:yellow;"></mark>&#x20;
  * <mark style="color:green;">HTTP, HTTPS, TCP, SSL (secure TCP)</mark>&#x20;
* <mark style="color:yellow;">**Application Load Balancer (v2 - new generation) – 2016 – ALB**</mark>** **&#x20;
  * <mark style="color:green;">HTTP, HTTPS, WebSocket</mark>&#x20;
* <mark style="color:yellow;">**Network Load Balancer (v2 - new generation) – 2017 – NLB**</mark> <mark style="color:yellow;"></mark><mark style="color:yellow;"></mark>&#x20;
  * <mark style="color:green;">TCP, TLS (secure TCP), UDP</mark>&#x20;
* <mark style="color:yellow;">**Gateway Load Balancer – 2020 – GWLB**</mark>** **&#x20;
  * <mark style="color:green;">Operates at layer 3 (Network layer) – IP Protocol</mark>&#x20;
* Overall, it is recommended to use the newer generation load balancers as they provide more features.&#x20;
* Some load balancers can be setup as internal (private) or external (public) ELBs.

## Security Groups in Load Balancer

<figure><img src="../../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>
