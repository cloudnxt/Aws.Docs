---
description: Layer 3
---

# Gateway Load Balancer

* Deploy, scale, and manage a fleet of 3rd party network virtual appliances in AWS&#x20;
* Example: Firewalls, Intrusion Detection and Prevention Systems, Deep Packet Inspection Systems, payload manipulation, …&#x20;
* Operates at Layer 3 (Network Layer) – IP Packets&#x20;
* Combines the following functions:&#x20;
  * **Transparent Network Gateway** – single entry/exit for all traffic&#x20;
  * **Load Balancer** – distributes traffic to your virtual appliances&#x20;
* Uses the **GENEVE** protocol on port **6081**

## Target Groups for GLB

* EC2 instances.&#x20;
* IP Addresses – must be private IPs.

<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>
