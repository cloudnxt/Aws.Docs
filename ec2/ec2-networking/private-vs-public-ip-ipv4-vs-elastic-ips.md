---
description: Identity within a network.
---

# Private vs Public IP (IPv4) vs Elastic IPs

* Networking has two sorts of IPs. IPv4 and IPv6:&#x20;
  * IPv4: 1.160.10.240&#x20;
  * IPv6: 3ffe:1900:4545:3:200:f8ff:fe21:67cf&#x20;
* IPv4 is still the most common format used online.&#x20;
* IPv6 is newer and solves problems for the Internet of Things (IoT).&#x20;
* IPv4 allows for 3.7 billion different addresses in the public space.&#x20;
* IPv4: \[0-255].\[0-255].\[0-255].\[0-255]

## Private vs Public IP (IPv4) vs Elastic IPs Fundamental Differences&#x20;

### Public IP:&#x20;

* Public IP means the machine can be identified on the internet (WWW).&#x20;
* Must be unique across the whole web (not two machines can have the same public IP).
* Can be geo-located easily.&#x20;

### Private IP:&#x20;

* Private IP means the machine can only be identified on a private network only&#x20;
* The IP must be unique across the private network.&#x20;
* BUT two different private networks (two companies) can have the same IPs.&#x20;
* Machines connect to WWW using a NAT + internet gateway (a proxy)&#x20;
* Only a specified range of IPs can be used as private IP.

### Elastic IPs:

* When you stop and then start an EC2 instance, it can change its public IP.&#x20;
* If you need to have a fixed public IP for your instance, you need an Elastic IP&#x20;
* An Elastic IP is a public IPv4 IP you own as long as you don’t delete it.
* You can attach it to one instance at a time.
* With an Elastic IP address, you can mask the failure of an instance or software by rapidly remapping the address to another instance in your account.
* You can only have 5 Elastic IP in your account (you can ask AWS to increase that).
* <mark style="color:red;">Overall, try to avoid using Elastic IP</mark>:&#x20;
  * They often reflect poor architectural decisions.&#x20;
  * Instead, use a random public IP and register a DNS name to it.&#x20;
  * Or, as we’ll see later, use a Load Balancer and don’t use a public IP.

## IP's In AWS EC2

> <mark style="color:yellow;">If your machine is stopped and then started, the public IP can change.</mark>

*   By default, your EC2 machine comes with:&#x20;

    * A private IP for the internal AWS Network&#x20;
    * A public IP, for the WWW.

    When we are doing SSH into our EC2 machines:&#x20;

    * We can’t use a private IP, because we are not in the same network.&#x20;
    * We can only use the public IP.

    <mark style="color:yellow;"></mark>
