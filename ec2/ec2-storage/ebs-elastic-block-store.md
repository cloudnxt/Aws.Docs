---
description: Think of them as a “network USB stick”
---

# EBS - Elastic Block Store



* An EBS (Elastic Block Store) Volume is a network drive you can attach to your instances while they run.
* It allows your instances to persist data, even after their termination.
* They can only be mounted to one instance at a time (at the CCP level)
* <mark style="color:yellow;">They are bound to a specific availability zone.</mark>
* <mark style="color:orange;">Free tier: 30 GB of free EBS storage of type General Purpose (SSD) or Magnetic per month</mark>
* <mark style="color:green;">It’s a network drive (i.e not a physical drive)</mark>&#x20;
* <mark style="color:green;">It uses the network to communicate the instance, which means there might be a bit of latency.</mark>&#x20;
* <mark style="color:green;">It can be detached from an EC2 instance and attached to another one quickly.</mark>&#x20;
* <mark style="color:red;">An EBS Volume in us-east-1a cannot be attached to us-east-1b</mark>&#x20;
* To move a volume across, you first need to snapshot it.&#x20;
* Have a provisioned capacity (size in GBs, and IOPS)&#x20;
* You get billed for all the provisioned capacity • You can increase the capacity of the drive over time.

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

## EBS – Delete on Termination attribute

* Controls the EBS behaviour when an EC2 instance terminates.&#x20;
* <mark style="color:yellow;">By</mark> <mark style="color:yellow;"></mark><mark style="color:yellow;">**default**</mark><mark style="color:yellow;">, the root EBS volume is deleted (attribute enabled)</mark>&#x20;
* <mark style="color:yellow;">By</mark> <mark style="color:yellow;"></mark><mark style="color:yellow;">**default**</mark><mark style="color:yellow;">, any other attached EBS volume is not deleted (attribute disabled)</mark>

## EBS Volume Types

* EBS Volumes come in 6 types:&#x20;
  * <mark style="color:yellow;">gp2 / gp3 (SSD)</mark>: General purpose SSD volume that balances price and performance for a wide variety of workloads.&#x20;
  * <mark style="color:yellow;">io1 / io2 (SSD)</mark>: Highest-performance SSD volume for mission-critical low-latency or high-throughput workloads&#x20;
  * <mark style="color:yellow;">st1 (HDD)</mark>: Low-cost HDD volume designed for frequently accessed, throughput- intensive workloads.&#x20;
  * <mark style="color:yellow;">sc1 (HDD)</mark>: Lowest cost HDD volume designed for less frequently accessed workloads.&#x20;
* EBS Volumes are characterized in Size | Throughput | IOPS (I/O Ops Per Sec)&#x20;
* When in doubt always consult the AWS documentation – it’s good!&#x20;
* Only gp2/gp3 and io1/io2 can be used as boot volumes.

### General Purpose SSD - <mark style="color:yellow;">gp2 / gp3 (SSD)</mark>

* Cost effective storage, low-latency.&#x20;
* System boot volumes, Virtual desktops, Development and test environments&#x20;
* <mark style="color:green;">1 GiB - 16 TiB</mark>&#x20;
* gp3:&#x20;
  * Baseline of 3,000 IOPS and throughput of 125 MiB/s&#x20;
  * Can increase IOPS up to 16,000 and throughput up to 1000 MiB/s independently.&#x20;
* gp2:&#x20;
  * Small gp2 volumes can burst IOPS to 3,000&#x20;
  * Size of the volume and IOPS are linked, max IOPS is 16,000&#x20;
  * 3 IOPS per GB, means at 5,334 GB we are at the max IOPS.

### Provisioned IOPS (PIOPS) SSD - <mark style="color:yellow;">io1 / io2 (SSD)</mark>

* Critical business applications with sustained IOPS performance&#x20;
* Or applications that need more than 16,000 IOPS&#x20;
* Great for databases workloads (sensitive to storage perf and consistency)&#x20;
* io1/io2 (4 GiB - 16 TiB):&#x20;
* Max PIOPS: 64,000 for Nitro EC2 instances & 32,000 for other&#x20;
* Can increase PIOPS independently from storage size.&#x20;
* io2 have more durability and more IOPS per GiB (at the same price as io1)&#x20;
* io2 Block Express (4 GiB – 64 TiB): • Sub-millisecond latency&#x20;
* Max PIOPS: 256,000 with an IOPS:GiB ratio of 1,000:1&#x20;
* <mark style="color:green;">Supports EBS Multi-attach.</mark>

#### EBS Multi-Attach – io1/io2 family

* <mark style="color:green;">Attach the same EBS volume to multiple EC2 instances in the same AZ.</mark>&#x20;
* Each instance has full read & write permissions to the high-performance volume.&#x20;
* Use case:&#x20;
* Achieve higher application availability in clustered Linux applications (ex: Teradata)&#x20;
* Applications must manage concurrent write operations.&#x20;
* Up to 16 EC2 Instances at a time&#x20;
*   Must use a file system that’s cluster-aware (not XFS, EX4, etc.)



<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption><p>io2 Multi Attach</p></figcaption></figure>

### Hard Disk Drives (HDD)

{% hint style="info" %}
Cannot be a boot volume.
{% endhint %}

* 125 GiB to 16 TiB&#x20;
* Throughput Optimized HDD (st1)&#x20;
  * Big Data, Data Warehouses, Log Processing&#x20;
  * <mark style="color:yellow;">Max throughput 500 MiB/s – max IOPS 500</mark>&#x20;
* Cold HDD (sc1):&#x20;
  * For data that is infrequently accessed&#x20;
  * Scenarios where lowest cost is important&#x20;
  * <mark style="color:yellow;">Max throughput 250 MiB/s – max IOPS 250</mark>

## EBS Encryption

* When you create an encrypted EBS volume, you get the following:&#x20;
  * Data at rest is encrypted inside the volume.&#x20;
  * All the data in flight moving between the instance and the volume is encrypted.&#x20;
  * All snapshots are encrypted.&#x20;
  * All volumes created from the snapshot are encrypted.&#x20;
* Encryption and decryption are handled transparently (you have nothing to do)&#x20;
* Encryption has a minimal impact on latency&#x20;
* EBS Encryption leverages keys from KMS (AES-256)&#x20;
* Copying an unencrypted snapshot allows encryption.&#x20;
* <mark style="color:green;">Snapshots of encrypted volumes are encrypted.</mark>

### More about Encryption

* Encryption: encrypt an unencrypted EBS volume
  * Create an EBS snapshot of the volume.&#x20;
  * Encrypt the EBS snapshot (using copy)&#x20;
  * Create new EBS volume from the snapshot (the volume will also be encrypted)&#x20;
  * Now you can attach the encrypted volume to the original instance.

## EBS –Volume Types Summary

{% embed url="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html" %}

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

## EBS Snapshots

* Make a backup (snapshot) of your EBS volume at a point in time.
* <mark style="color:yellow;">Not necessary to detach volume to do snapshot but recommended.</mark>
* <mark style="color:yellow;">Can copy snapshots across AZ or Region</mark>

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption><p>Copy Snapshot across AZ</p></figcaption></figure>

## EBS Snapshots Features

### EBS Snapshot Archive

* Move a Snapshot to an ”archive tier” that is 75% cheaper.&#x20;
* Takes within 24 to 72 hours for restoring the archive.

### Recycle Bin for EBS Snapshots

* Setup rules to retain deleted snapshots so you can recover them after an accidental deletion.
* Specify retention (from 1 day to 1 year)

## Fast Snapshot Restore (FSR)

* Force full initialization of snapshot to have no latency on the first use (\$$$)
