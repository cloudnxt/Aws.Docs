# EC2 - Sizing & configurations

* Operating System (OS): Linux, Windows or Mac OS&#x20;
* How much compute power & cores (CPU)&#x20;
* How much random-access memory (RAM)&#x20;
* How much storage space:&#x20;
  * Network-attached (EBS & EFS)&#x20;
  * hardware (EC2 Instance Store)&#x20;
* Network card: speed of the card, Public IP address&#x20;
* Firewall rules: security group&#x20;
* Bootstrap script (configure at first launch): [EC2 User Data](ec2-sizing-and-configurations.md#ec2-user-data)

## Sizing

You can use different types of EC2 instances that are optimised for different use cases ([https://aws.amazon.com/ec2/instance-types/](https://aws.amazon.com/ec2/instance-types/))

<mark style="color:blue;">**m**</mark><mark style="color:orange;">**5**</mark>**.**<mark style="color:green;">**2xlarge**</mark>

* <mark style="color:blue;">**m**</mark>: instance class&#x20;
* <mark style="color:orange;">**5**</mark>: generation (AWS improves them over time)&#x20;
* <mark style="color:green;">**2xlarge**</mark>: size within the instance class

## EC2 Instance Types

### General Purpose

Great for a diversity of workloads such as web servers or code repositories&#x20;

Balance between:&#x20;

* Compute&#x20;
* Memory&#x20;
* Networking

### Compute Optimized

### Memory Optimized

### Storage Optimized

### Some T2 type examples

| Instance   | vCPU\* | <p>CPU Credits / hour<br></p> | Mem (GiB) | <p> Storage<br></p> | Network Performance |
| ---------- | ------ | ----------------------------- | --------- | ------------------- | ------------------- |
| t2.nano    | 1      | 3                             | 0.5       | EBS-Only            | Low                 |
| t2.micro   | 1      | 6                             | 1         | <p>EBS-Only<br></p> | Low to Moderate     |
| t2.small   | 1      | 12                            | 2         | <p>EBS-Only<br></p> | Low to Moderate     |
| t2.medium  | 2      | 24                            | 4         | <p>EBS-Only<br></p> | Low to Moderate     |
| t2.large   | 2      | 36                            | 8         | EBS-Only            | Low to Moderate     |
| t2.xlarge  | 4      | 54                            | 16        | EBS-Only            | Moderate            |
| t2.2xlarge | 8      | 81                            | 32        | EBS-Only            | Moderate            |

## EC2 User Data

* It is possible to bootstrap our instances using an EC2 User data script.&#x20;
* bootstrapping means launching commands when a machine starts.&#x20;
* That script is <mark style="color:green;">only run once</mark> at the instance first start.&#x20;
* EC2 user data is used to automate boot tasks such as:&#x20;
  * Installing updates&#x20;
  * Installing software&#x20;
  * Downloading common files from the internet&#x20;
  * Anything you can think of&#x20;
* The EC2 User Data Script <mark style="color:green;">runs with the root user</mark>.
