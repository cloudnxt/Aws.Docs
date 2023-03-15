# ELB - SSL Certificates

## What is SSL?

* An SSL Certificate allows traffic between your clients and your load balancer to be encrypted in transit (in-flight encryption).
* SSL refers to Secure Sockets Layer, used to encrypt connections.&#x20;
* TLS refers to Transport Layer Security, which is a newer version.&#x20;
* Nowadays, TLS certificates are mainly used, but people still refer as SSL.
* Public SSL certificates are issued by Certificate Authorities (CA)&#x20;
* Comodo, Symantec, GoDaddy, GlobalSign, DigiCert, Letsencrypt, etc.
* SSL certificates have an expiration date (you set) and must be renewed.

## Load Balancer - SSL Certificates

* The load balancer uses an X.509 certificate (SSL/TLS server certificate)&#x20;
* You can manage certificates using ACM (AWS Certificate Manager)&#x20;
* You can create upload your own certificates alternatively.&#x20;
* HTTPS listener:&#x20;
  * You must specify a default certificate&#x20;
  * You can add an optional list of certs to support multiple domains&#x20;
  * Clients can use SNI (Server Name Indication) to specify the hostname they reach&#x20;
  * Ability to specify a security policy to support older versions of SSL / TLS (legacy clients)

### **Classic Load Balancer (v1)**&#x20;

• <mark style="color:green;">Support only one SSL certificate</mark>&#x20;

• Must use multiple CLB for multiple hostname with multiple SSL certificates •&#x20;

### **Application Load Balancer (v2)**&#x20;

• <mark style="color:green;">Supports multiple listeners with multiple SSL certificates</mark>&#x20;

• Uses Server Name Indication (SNI) to make it work&#x20;

### **Network Load Balancer (v2)**&#x20;

• <mark style="color:green;">Supports multiple listeners with multiple SSL certificates</mark>&#x20;

• Uses Server Name Indication (SNI) to make it work

## SSL – Server Name Indication (SNI)

{% hint style="info" %}
<mark style="color:yellow;">Only works for ALB & NLB (newer generation), CloudFront</mark>&#x20;

<mark style="color:yellow;">Does not work for CLB (older gen)</mark>
{% endhint %}

* SNI solves the problem of loading multiple SSL certificates onto one web server (to serve multiple websites)&#x20;
* It’s a “newer” protocol and requires the client to indicate the hostname of the target server in the initial SSL handshake.&#x20;
* The server will then find the correct certificate or return the default one.

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>
