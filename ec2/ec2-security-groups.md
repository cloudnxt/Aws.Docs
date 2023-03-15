---
description: Securing Network
---

# EC2 - Security Groups

* Security Groups are the fundamental of network security in AWS.&#x20;
* They control how traffic is allowed into or out of our EC2 Instances.&#x20;
* Security groups only contain rules.&#x20;
* Security groups rules can reference by IP or by security group.
* Security groups are acting as a “firewall” on EC2 instances.
* They regulate:&#x20;
  * Access to Ports&#x20;
  * Authorized IP ranges – IPv4 and IPv6&#x20;
  * Control of inbound network (from other to the instance)&#x20;
  * Control of outbound network (from the instance to other

## Key Things to Know

* Can be attached to multiple instances.&#x20;
* Locked down to a region / VPC combination.&#x20;
* Does live “outside” the EC2 – if traffic is blocked the EC2 instance won’t see it.
* It’s good to maintain one separate security group for SSH access.
* If your application is not accessible (time out), then it’s a security group issue.&#x20;
* If your application gives a “connection refused error", then it’s an application error or it’s not launched.
* All inbound traffic is blocked by default.
* All outbound traffic is authorized by default.

## Define Security Group Rule

For each rule, you specify the following:

*   **Name**: The name for the security group (for example, "my-security-group").

    A name can be up to 255 characters in length. Allowed characters are a-z, A-Z, 0-9, spaces, and .\_-:/()#,@\[]+=;{}!$\*. When the name contains trailing spaces, we trim the spaces when we save the name. For example, if you enter "Test Security Group " for the name, we store it as "Test Security Group".
* **Protocol**: The protocol to allow. The most common protocols are 6 (TCP), 17 (UDP), and 1 (ICMP).
* **Port range**: For TCP, UDP, or a custom protocol, the range of ports to allow. You can specify a single port number (for example, `22`), or range of port numbers (for example, `7000-8000`).
* **ICMP type and code:** For ICMP, the ICMP type and code. For example, use type 8 for ICMP Echo Request or type 128 for ICMPv6 Echo Request.
* **Source or destination:** The source (inbound rules) or destination (outbound rules) for the traffic to allow. Specify one of the following:
  * A single IPv4 address. You must use the `/32` prefix length. For example, `203.0.113.1/32`.
  * A single IPv6 address. You must use the `/128` prefix length. For example, `2001:db8:1234:1a00::123/128`.
  * A range of IPv4 addresses, in CIDR block notation. For example, `203.0.113.0/24`.
  * A range of IPv6 addresses, in CIDR block notation. For example, `2001:db8:1234:1a00::/64`.
  * The ID of a prefix list. For example, `pl-1234abc1234abc123`. For more information, see [Prefix lists](https://docs.amazonaws.cn/vpc/latest/userguide/managed-prefix-lists.html) in the _Amazon VPC User Guide_.
  * The ID of a security group (referred to here as the specified security group). For example, the current security group, a security group from the same VPC, or a security group for a peered VPC. This allows traffic based on the private IP addresses of the resources associated with the specified security group. This does not add rules from the specified security group to the current security group.

## Example Security Group

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption><p>Sample Security group</p></figcaption></figure>

The above Security group setup will work as below. It would allow traffic to pass from only one source if its **SSH**. **HTTP** Traffic on port **80** is allowed from anywhere. Alos, HTTP traffic to the java app running on port **4567** is also accessible outside.

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption><p>Security Groups Diagram</p></figcaption></figure>

## Referencing other security groups Diagram

A security group can be configured to bind to other security group in the source section of the rule. When attached, it would allow traffic from those security groups too. To know more how it's done read [here](ec2-security-groups.md#define-security-group-rule)

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

## Classic Ports to know.&#x20;

* 22 = SSH (Secure Shell) - log into a Linux instance&#x20;
* 21 = FTP (File Transfer Protocol) – upload files into a file share&#x20;
* 22 = SFTP (Secure File Transfer Protocol) – upload files using SSH&#x20;
* 80 = HTTP – access unsecured websites&#x20;
* 443 = HTTPS – access secured websites&#x20;
* 3389 = RDP (Remote Desktop Protocol) – log into a Windows instance

