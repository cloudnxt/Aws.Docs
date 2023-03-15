---
description: Logical component in a VPC that represents a virtual network card.
---

# Elastic Network Interfaces (ENI)

{% hint style="info" %}
<mark style="color:yellow;">When you create your own ENI, Deleting the EC2 would not delete the ENI.</mark>
{% endhint %}

To Know more on this topic: [https://aws.amazon.com/blogs/aws/new-elastic-network-interfaces-in-the-virtual-private-cloud/](https://aws.amazon.com/blogs/aws/new-elastic-network-interfaces-in-the-virtual-private-cloud/)

* The ENI can have the following attributes:&#x20;
  * Primary private IPv4, one or more secondary IPv4.&#x20;
  * One Elastic IP (IPv4) per private IPv4.
  * One Public IPv4.
  * One or more security groups.&#x20;
  * A MAC address.
* You can create ENI independently and attach them on the fly (move them) on EC2 instances for failover.
* <mark style="color:yellow;">Bound to a specific availability zone (AZ)</mark>

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption><p>Attaching and detaching an ENI</p></figcaption></figure>
