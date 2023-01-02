depending on the service, your resources are either deployed at the AZ, region, or global level

### Region-scoped services
- you only select the region you want to use
- if you are not asked to specify an individual AZ to deploy the service in, this indicates the service operates on a region-scope level
- for region-scoped services, AWS automatically performs actions to increase data durability and availability

with services that ask you to specify an AZ, you are often responsible for increasing the data durability and high availability of these resources