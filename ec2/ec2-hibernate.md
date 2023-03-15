---
description: Introducing EC2 Hibernate, save the state.
---

# EC2 - Hibernate

* We know we can stop, terminate instances.
  * Stop – the data on disk (EBS) is kept intact in the next start.
  * Terminate – any EBS volumes (root) also set-up to be destroyed is lost.
* On start, the following happens:
  * First start: the OS boots & the EC2 User Data script is run.&#x20;
  * Following starts: the OS boots up.&#x20;
  * Then your application starts, caches get warmed up, and that can take time!
* On Hibernate.
  * The in-memory (RAM) state is preserved
  * The instance boot is much faster! (the OS is not stopped / restarted)
  * Under the hood: the RAM state is written to a file in the root EBS volume.
  * <mark style="color:yellow;">The root EBS volume must be</mark> <mark style="color:yellow;"></mark><mark style="color:yellow;">**encrypted**</mark>

### Use cases:&#x20;

* Long-running processing&#x20;
* Saving the RAM state&#x20;
* Services that take time to initialize

## Good to know:

* Supported Instance Families – C3, C4, C5, I3, M3, M4, R3, R4, T2, T3, …
* Instance RAM Size – <mark style="color:yellow;">must be less than 150 GB</mark>.&#x20;
* Instance Size – <mark style="color:yellow;">not supported for bare metal instances</mark>.&#x20;
* AMI – Amazon Linux 2, Linux AMI, Ubuntu, RHEL, CentOS & Windows…&#x20;
* Root Volume – must be EBS, encrypted, not instance store, and large&#x20;
* Available for On-Demand, Reserved and Spot Instances&#x20;
* An instance <mark style="color:yellow;">can NOT be hibernated more than 60 days</mark>

