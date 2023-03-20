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
