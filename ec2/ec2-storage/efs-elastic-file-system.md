---
description: Managed NFS (network file system) that can be mounted on many EC2
---

# EFS - Elastic File System

* Managed NFS (network file system) that can be mounted on many EC2.
* EFS works with EC2 instances in multi-AZ.
* Highly available, scalable, expensive (3x gp2), pay per use.
* Use cases: content management, web serving, data sharing, Wordpress.&#x20;
* <mark style="color:green;">Uses NFSv4.1 protocol.</mark>&#x20;
* <mark style="color:green;">Uses security group to control access to EFS.</mark>&#x20;
* <mark style="color:green;">Compatible with Linux based AMI (not Windows)</mark>&#x20;
* Encryption at rest using KMS.&#x20;
* POSIX file system (\~Linux) that has a standard file API.&#x20;
* File system scales automatically, pay-per-use, no capacity planning!

<figure><img src="../../.gitbook/assets/image (27).png" alt=""><figcaption><p>Multi AZ EFS</p></figcaption></figure>

## EFS – Performance & Storage Classes

* **EFS Scale**&#x20;
  * 1000s of concurrent NFS clients, 10 GB+ /s throughput&#x20;
  * Grow to Petabyte-scale network file system, automatically.&#x20;
* **Performance Mode (set at EFS creation time)**&#x20;
  * **General Purpose (default)** – latency-sensitive use cases (web server, CMS, etc.)&#x20;
  * **Max I/O** – higher latency, throughput, highly parallel (big data, media processing)&#x20;
* **Throughput Mode**&#x20;
  * **Bursting** – 1 TB = 50MiB/s + burst of up to 100MiB/s&#x20;
  * **Provisioned** – set your throughput regardless of storage size, ex: 1 GiB/s for 1 TB storage.&#x20;
  * **Elastic** – automatically scales throughput up or down based on your workloads.&#x20;
    * Up to 3GiB/s for reads and 1GiB/s for writes.&#x20;
    * Used for unpredictable workloads.

## EFS – Storage Classes

* Storage Tiers (lifecycle management feature – move file after N days)&#x20;
* Standard: for frequently accessed files&#x20;
* Infrequent access (EFS-IA): cost to retrieve files, lower price to store. Enable EFS -IA with a Lifecycle Policy&#x20;
* Availability and durability&#x20;
* Standard: Multi-AZ, great for prod&#x20;
* One Zone: One AZ, great for dev, backup enabled by default, compatible with IA (EFS One Zone -IA).&#x20;
* Over 90% in cost savings.

<figure><img src="../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

