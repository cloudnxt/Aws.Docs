# ELB - Health Checks

* Health Checks are crucial for Load Balancers.&#x20;
* They enable the load balancer to know if instances it forwards traffic to are available to reply to requests.&#x20;
* The health check is done on a port and a route (/health is common).&#x20;
* If the response is not 200 (OK), then the instance is unhealthy.

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption><p>Health check</p></figcaption></figure>
