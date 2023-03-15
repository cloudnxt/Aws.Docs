# EC2 - ELB

Load Balances are servers that forward traffic to multiple servers (e.g., EC2 instances) downstream.

<figure><img src="../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

## Why use a load balancer?

* Spread load across multiple downstream instances.&#x20;
* Expose a single point of access (DNS) to your application.&#x20;
* Seamlessly handle failures of downstream instances.
* Do regular health checks to your instances.&#x20;
* Provide SSL termination (HTTPS) for your websites.&#x20;
* Enforce stickiness with cookies&#x20;
* High availability across zones • Separate public traffic from private traffi
