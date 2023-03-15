# EC2 - Placement groups

* Sometimes <mark style="color:yellow;">you want control over the EC2 Instance placement strategy</mark>.
* That strategy can be defined using placement groups.
* When you create a placement group, you specify one of the following strategies for the group.
  * <mark style="color:green;">**Cluster**</mark>** -** clusters instances into a low-latency group in a single Availability Zone&#x20;
  * <mark style="color:green;">**Spread**</mark>** -** spreads instances across underlying hardware (max 7 instances per group per AZ)&#x20;
  * <mark style="color:green;">**Partition**</mark>** -** spreads instances across many different partitions (which rely on different sets of racks) within an AZ. Scales to 100s of EC2 instances per group (Hadoop, Cassandra, Kafka)

## Cluster - Placement Group

<mark style="color:green;">Pros:</mark>&#x20;

* Great network (10 Gbps bandwidth between instances with Enhanced Networking enabled - recommended)

<mark style="color:red;">Cons:</mark>

* If the rack fails, all instances fail at the same time.

<mark style="color:yellow;">Use case:</mark>

* Big Data job that needs to complete fast&#x20;
* Application that needs extremely low latency and high network throughput

## Spread- Placement Group

<mark style="color:green;">Pros:</mark>

* Can span across Availability Zones (AZ)&#x20;
* Reduced risk is simultaneous failure.&#x20;
* EC2 Instances are on different physical hardware.

<mark style="color:red;">Cons:</mark>&#x20;

* Limited to 7 instances per AZ per placement group.

<mark style="color:yellow;">Use case:</mark>

* Application that needs to maximize high availability.&#x20;
* Critical Applications where each instance must be isolated from failure from each other.

## Partition - Placement Group

<mark style="color:green;">Pros:</mark>

* Can span across multiple AZs in the same region.
* The instances in a partition do not share racks with the instances in the other partitions.
* Up to 100s of EC2 instances
* A partition failure can affect many EC2 but won’t affect other partitions.
* EC2 instances get access to the partition information as metadata.

<mark style="color:red;">Cons:</mark>&#x20;

* Up to 7 partitions per AZ

<mark style="color:yellow;">Use case:</mark>

* HDFS, HBase, Cassandra, Kafka.
* Critical Applications where at least one instance or more need to be available at any time and in any case.
