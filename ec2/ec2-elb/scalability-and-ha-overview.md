# Scalability & HA Overview

* Scalability means that an application / system can handle greater loads by adapting.
* There are two kinds of scalability:&#x20;
  * <mark style="color:green;">Vertical Scalability</mark>&#x20;
  * <mark style="color:green;">Horizontal Scalability (= elasticity)</mark>&#x20;
* Scalability is linked but different to High Availability&#x20;
* Let’s deep dive into the distinction, using a call center as an example.

## Vertical Scalability&#x20;

* Vertically scalability means increasing the size of the instance&#x20;
* For example, your application runs on a t2.micro&#x20;
* Scaling that application vertically means running it on a t2.large&#x20;
* Vertical scalability is very common for non-distributed systems, such as a database.&#x20;
* RDS, ElastiCache are services that can scale vertically.&#x20;
* There’s usually a limit to how much you can vertically scale (hardware limit)

## Horizontal Scalability&#x20;

* Horizontal Scalability means increasing the number of instances / systems for your application.&#x20;
* Horizontal scaling implies distributed systems.&#x20;
* This is very common for web applications / modern applications.&#x20;
* It’s easy to horizontally scale thanks the cloud offerings such as Amazon EC2

## High Availability&#x20;

* High Availability usually goes hand in hand with horizontal scaling.&#x20;
* High availability means running your application / system in at least 2 data centers (== Availability Zones)&#x20;
* The goal of high availability is to survive a data center loss&#x20;
* The high availability can be passive (for RDS Multi AZ for example)&#x20;
* The high availability can be active (for horizontal scaling)

## High Availability & Scalability for EC2

* Vertical Scaling: Increase instance size (= scale up / down)&#x20;
  * From: t2.nano - 0.5G of RAM, 1 vCPU&#x20;
  * To: u-12tb1.metal – 12.3 TB of RAM, 448 vCPUs&#x20;
* Horizontal Scaling: Increase number of instances (= scale out / in)&#x20;
  * Auto Scaling Group&#x20;
  * Load Balancer
* High Availability: Run instances for the same application across multi AZ&#x20;
  * Auto Scaling Group multi-AZ.
  * Load Balancer multi-AZ.
