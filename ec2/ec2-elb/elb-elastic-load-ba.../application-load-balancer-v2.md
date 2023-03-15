---
description: Layer 4 & Layer 7
---

# Application Load Balancer (v2)

* Application load balancers is Layer 7 (HTTP)&#x20;
* Load balancing to multiple HTTP applications across machines (target groups)&#x20;
* Load balancing to multiple applications on the same machine (ex: containers)&#x20;
* Support for HTTP/2 and WebSocket&#x20;
* Support redirects (from HTTP to HTTPS for example)
* Routing tables to different target groups:&#x20;
  * Routing based on path in URL (example.com<mark style="color:yellow;">**/users**</mark> & example.com<mark style="color:yellow;">**/posts**</mark>)&#x20;
  * Routing based on hostname in URL (<mark style="color:yellow;">**one.example.com**</mark> & <mark style="color:yellow;">**other.example.com**</mark>)&#x20;
  * Routing based on Query String, Headers (example.com/users?<mark style="color:yellow;">**id=123\&order=false**</mark>)
* ALB are a great fit for micro services & container-based application (example: Docker & Amazon ECS)
* Has a port mapping feature to redirect to a dynamic port in ECS.
* In comparison, we’d need <mark style="color:red;">multiple</mark> [<mark style="color:red;">**Classic Load Balancer**</mark>](classic-load-balancers-v1.md) <mark style="color:red;">per application</mark>.

## Possible Target Groups of ALB

* <mark style="color:green;">**EC2 instances**</mark> (can be managed by an Auto Scaling Group) – HTTP&#x20;
* <mark style="color:green;">**ECS tasks**</mark> (managed by ECS itself) – HTTP&#x20;
* <mark style="color:green;">**Lambda functions**</mark> – HTTP request is translated into a JSON event&#x20;
* <mark style="color:green;">**IP Addresses**</mark> – must be private IPs

{% hint style="info" %}
* <mark style="color:green;">ALB can route to multiple target groups.</mark>
* <mark style="color:green;">Health checks are at the target group level.</mark>
{% endhint %}

## Good to Know

* Fixed hostname (XXX.region.elb.amazonaws.com)
* The application servers don’t see the IP of the client directly&#x20;
  * The true IP of the client is inserted in the header <mark style="color:orange;">**X-Forwarded-For**</mark>&#x20;
  * We can also get Port (<mark style="color:orange;">**X-Forwarded-Port**</mark>) and proto (<mark style="color:orange;">**X-Forwarded-Proto**</mark>)

## HTTP Based Traffic

<figure><img src="../../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

## Query Strings/Parameters Routing

<figure><img src="../../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

