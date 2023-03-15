---
description: What's the difference. ?
---

# EBS vs EFS

* EBS volumes…&#x20;
  * one instance (except multi-attach io1/io2)&#x20;
  * are locked at the Availability Zone (AZ) level.&#x20;
  * gp2: IO increases if the disk size increases.&#x20;
  * io1: can increase IO independently.&#x20;
* To migrate an EBS volume across AZ&#x20;
  * Take a snapshot.&#x20;
  * Restore the snapshot to another AZ.&#x20;
  * EBS backups use IO and you shouldn’t run them while your application is handling a lot of traffic.&#x20;
* Root EBS Volumes of instances get terminated by default if the EC2 instance gets terminated. (You can disable that)

<img src="../../.gitbook/assets/image (11).png" alt="" data-size="original">![](<../../.gitbook/assets/image (19).png>)

* Mounting 100s of instances across AZ&#x20;
* EFS share website files (WordPress)&#x20;
* Only for Linux Instances (POSIX)&#x20;
* EFS has a higher price point than EBS&#x20;
* Can leverage EFS-IA for cost savings&#x20;
* Remember: EFS vs EBS vs Instance Store
