---
description: Wait for a bit.
---

# ELB - Connection Draining

* **Feature naming**&#x20;
  * Connection Draining – for CLB&#x20;
  * Deregistration Delay – for ALB & NLB
* Time to complete “in-flight requests” while the instance is de-registering or unhealthy.&#x20;
* Stops sending new requests to the EC2 instance which is de-registering • Between 1 to 3600 seconds (default: 300 seconds)&#x20;
* <mark style="color:green;">Can be disabled (set value to 0)</mark>&#x20;
* Set to a low value if your requests are short.

