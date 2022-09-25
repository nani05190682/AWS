# AWS
Placement Group Strategies:
Types:
1. Cluster Placement Group
2. Partition Placement Group
3. Spread Placement Group

**Cluster placement groups**
*  Logical grouping of instances within a single Availability Zone.
* A cluster placement group can span peered VPCs in the same Region.
* Higher per-flow throughput limit for TCP/IP traffic and are placed in the same high-bisection bandwidth segment of the network.
* Recommended for applications that benefit from low network latency, high network throughput, or both. 

![img.png](img.png)

**Limitations**

Instance Supported: 

* Current generation instances, except for burstable performance instances (for example, T2) and Mac1 instances.
* A cluster placement group can't span multiple Availability Zones.
* The maximum network throughput speed of traffic between two instances in a cluster placement group is limited by the slower of the two instances. 
* Network traffic to the internet and over an AWS Direct Connect connection to on-premises resources is limited to 5 Gbps.

    


**Partition placement groups**

* Reduce the likelihood of correlated hardware failures for your application
* When using partition placement groups, Amazon EC2 divides each group into logical segments called partitions.
* Each partition within a placement group has its own set of racks. Each rack has its own network and power source.
* No two partitions within a placement group share the same racks, allowing you to isolate the impact of hardware failure within your application.

![img_1.png](img_1.png)

**Use Cases**:  deploy large distributed and replicated workloads, such as HDFS, HBase, and Cassandra, across distinct racks.

* A partition placement group can have partitions in multiple Availability Zones in the same Region.
* A partition placement group can have a maximum of seven partitions per Availability Zone. 
* . The number of instances that can be launched into a partition placement group is limited only by the limits of your account.

**Limitations**

* A partition placement group supports a maximum of seven partitions per Availability Zone. The number of instances that you can launch in a partition placement group is limited only by your account limits.
* When instances are launched into a partition placement group, Amazon EC2 tries to evenly distribute the instances across all partitions. Amazon EC2 doesn’t guarantee an even distribution of instances across all partitions.
* A partition placement group with Dedicated Instances can have a maximum of two partitions.


**Spread placement groups**

* A spread placement group is a group of instances that are each placed on distinct hardware.

![img_2.png](img_2.png)

