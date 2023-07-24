https://aws.amazon.com/about-aws/global-infrastructure/regions_az/

## Availability Zone
Inside every Region is a cluster of Availability Zones. An Availability Zone consists of one or more data centers with redundant power, networking, and connectivity. These data centers operate in discrete facilities in undisclosed locations. They are connected using redundant high-speed and low-latency links.

![AvailabilityZone](/Images/availabilityZone.jpg)


- **us-east-1a** is an Availability Zone in us-east-1 (N. Virginia Region).
- **sa-east-1b** is an Availability Zone in sa-east-1 (São Paulo Region).

Therefore, if you see that a resource exists in us-east-1c, you can infer that the resource is located in Availability Zone c of the us-east-1 Region.


## Region
![Region](/Images/Region.jpg)
How do you choose Region?
- Data [[Compliance]] ( must live in the UK boundaries etc..., choose London region)
- [[Latency]]( How close the resources are to the userbase) a big hurdle...
- [[Pricing]]
- [[Service availability]]


## Global Edge Network

Infrastructure, like data centers and networking connectivity, still exists as the foundation of every cloud application. In AWS, this physical infrastructure makes up the AWS Global Infrastructure, in the form of Regions and Availability Zones.

## 

**Regions**

![Region Map](/Images/RegionMap.JPEG)
Regions are geographic locations worldwide where AWS hosts its data centers. AWS Regions are named after the location where they reside. For example, in the United States, the Region in Northern Virginia is called the Northern Virginia Region, and the Region in Oregon is called the Oregon Region. AWS has Regions in Asia Pacific, China, Europe, the Middle East, North America, and South America. And we continue to expand to meet our customers' needs.****

Here are examples of Region codes:

- **us-east-1** is the first Region created in the eastern US area. The geographical name for this Region is N. Virginia.
- **ap-northeast-1** is the first Region created in the northeast Asia Pacific area. The geographical name for this Region is Tokyo.

### 

**Choosing the right AWS Region**

==AWS Regions are independent from one another.== Without explicit customer consent and authorization, data is not replicated from one Region to another. When you decide which AWS Region to host your applications and workloads, consider four main aspects: latency, price, service availability, and compliance.



## Scope of AWS services

Depending on the AWS service that you use, your resources are either deployed at the Availability Zone, Region, or Global level. Each service is different, so you must understand how the scope of a service might affect your application architecture.

## Maintaining resiliency

To keep your application available, you must maintain high availability and resiliency. A well-known best practice for cloud architecture is to use Region-scoped, managed services. These services come with availability and resiliency built in. When that is not possible, make sure your workload is replicated across multiple Availability Zones. At a minimum, you should use two Availability Zones. That way, if an Availability Zone fails, your application will have infrastructure up and running in a second Availability Zone to take over the traffic.

## Edge locations  

Edge locations are global locations where content is cached. For example, if your media content is in London and you want to share video files with your customers in Sydney, you could have the videos cached in an edge location closest to Sydney. This would make it possible for your customers to access the cached videos more quickly than accessing them from London. Currently, there are over 400+ edge locations globally.

Amazon CloudFront delivers your content through a worldwide network of edge locations. When a user requests content that is being served with CloudFront, the request is routed to the location that provides the lowest latency. So that content is delivered with the best possible performance. CloudFront speeds up the distribution of your content by routing each user request through the AWS backbone network to the edge location that can best serve your content.![[edge.png]]