Benefits
--------
- Pay as you go:
you only pay for when you are using computing resources, and pay only for how much you use

- Massive economies of scale:
you can achieve a lower cost than you can get on your own. Usage from hundreds of thousands of customers is aggregated in the cloud

- Stop guessing capacity:
You can access as much or as little capacity as you need, and scale up and down as required with only a few minutes notice.

- Increase speed and agility:
Reduction in the time to make resources available to your developers from weeks to minutes. Dramatic increase in agility for the organization since the cost and time it takes to experiment and develop is significantly lower

- Stop spending money running and maintaining data centers:
Cloud computing lets you focus on your customers, rather than on the heavy lifting of racking, stacking and powering physical infrastructure (undifferentiated heavy lifting)

- Go global in minutes
lower latency for your app by deploying your application to multiple regions around the world in minutes


Key terms:
- redundancy
a way to protect against natural disasters, etc. in order to minimize the loss of data; AWS connects data centers together in clusters through high speed and low latency links

- availabilty zone
cluster of data centers, if one data center goes down the other is available; one or more data centers with redundant power, networking and connectivity


- region
a cluster of availability zones (AZs)

4 aspects when deciding a region:
- compliance
- latency
- price
- service availability


### Compliance
Must look at compliance requirements, is there a requirement that data must reside in certain places?

### Latency
About how close your resources are to your userbase, infra that hosts the photos should be close to where the users are; otherwise slower load times could result; synchronous apps such as gaming, telephony, websockets, and IoT are significantly affected by higher latency, but even asynch workloads, such as ecommerce applications, can suffter from an impact on user connectivity

### Pricing
Can vary from region to region, some reasons may be more expensive than others due to taxes, internet connectivity, prices of imported pieces of equipment, customs, real estate etc.

### Service availability
New services aren't rolled out to every region right away