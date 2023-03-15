# EC2 Spot Instances



* Can get a <mark style="color:green;">discount of up to 90%</mark> compared to On-demand
* Instances that you can <mark style="color:red;">“lose” at any point of time</mark> if your max price is less than the current spot price&#x20;
* The <mark style="color:green;">MOST cost-efficient</mark> instances in AWS
* Useful for workloads that are resilient to failure&#x20;
  * Batch jobs&#x20;
  * Data analysis&#x20;
  * Image processing&#x20;
  * Any distributed workloads&#x20;
  * Workloads with a flexible start and end time&#x20;
* <mark style="color:red;">Not suitable for critical jobs or databases.</mark>

## EC2 Spot Instance Requests&#x20;

* <mark style="color:green;">Can get a discount of up to 90% compared to On-demand.</mark>&#x20;
* Define **max spot price** and get the instance while current spot price < max.&#x20;
  * The hourly spot price varies based on offer and capacity.&#x20;
  * If the current spot price > your max price you can choose to stop or terminate your instance with a 2 minute grace period.&#x20;
* Other strategy: **Spot Block**&#x20;
  * “block” spot instance during a specified time frame (1 to 6 hours) without interruptions&#x20;
  * In rare situations, the instance may be reclaimed.&#x20;
* <mark style="color:green;">Used for batch jobs, data analysis, or workloads that are resilient to failures.</mark>&#x20;
* <mark style="color:red;">Not great for critical jobs or databases.</mark>

## Terminating Spot Instances

{% hint style="info" %}
<mark style="color:yellow;">You can only cancel Spot Instance requests that are</mark> <mark style="color:yellow;"></mark><mark style="color:yellow;">**open**</mark><mark style="color:yellow;">,</mark> <mark style="color:yellow;"></mark><mark style="color:yellow;">**active**</mark><mark style="color:yellow;">, or</mark> <mark style="color:yellow;"></mark><mark style="color:yellow;">**disabled**</mark><mark style="color:yellow;">. Cancelling a Spot Request does not terminate instances</mark> <mark style="color:yellow;"></mark><mark style="color:yellow;"><mark style="color:orange;"><mark style="color:orange;"></mark> <mark style="color:yellow;"></mark><mark style="color:yellow;">You must first cancel a Spot Request, and then terminate the associated Spot Instances</mark>
{% endhint %}

<figure><img src="../../.gitbook/assets/image (28).png" alt=""><figcaption><p>Spot Instance Lifecycle</p></figcaption></figure>

## Spot Fleets

* Spot Fleets = set of Spot Instances + (optional) On-Demand Instances&#x20;
* The Spot Fleet will try to meet the target capacity with price constraints&#x20;
  * Define possible launch pools: instance type (m5.large), OS, Availability Zone&#x20;
  * Can have multiple launch pools, so that the fleet can choose&#x20;
  * Spot Fleet stops launching instances when reaching capacity or max cost&#x20;
* Strategies to allocate Spot Instances:&#x20;
  * lowestPrice: from the pool with the lowest price (cost optimization, short workload)&#x20;
  * diversified: distributed across all pools (great for availability, long workloads)&#x20;
  * capacityOptimized: pool with the optimal capacity for the number of instances&#x20;
* Spot Fleets allow us to automatically request Spot Instances with the lowest price
