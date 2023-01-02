You and AWS is ultimately responsible for securing the AWS environment

Shared Responsibility Model: security is a collection of parts that build on each other

AWS is responsible for security **of** the cloud
- Hardware/AWS global infrastructure (physical), private fiber cables that connect each region to each other
- securing compute, storage, database, networking services from the host operating system through virtualization
- the level of responsibility AWS has depends on the service
- categories:
 1. infrastructure services
 2. container services
 3. abstracted services

 infra services
 --------------
 - compute services (ie. ec2): aws manages the underlying infra and foundation services

 container services
 ------------------
 - services requiring less management from the customer (ie. rds): aws manages the underlying infra and foundation services, os and application platform

 abstracted services
 -------------------
 - services requiring little management from the customer (ie. s3): aws operates the infra layer, os, and platforms, server-side encryption and data protection



"You" are responsible for security **in** the cloud
- ec2: patching operating system of vms, encryptin the data in transit, configuring firewalls, and controlling who has access and how much access they have to resources
- properly configuring the service and your applications, as well as ensuring your data is secure
- the level of responsibility you have depends on the AWS service. some services require you to perform all of the necessary security configuration and management tasks, while others require you to only manage the data and control access to your resources

infra services
--------------
- AWS: infra and foundation services
- you control the operating system and application platform, as well as encrypting, protecting and managing customer data
 

container services
------------------
- AWS: manages the infra and foundation services, os, and application platform
- you are responsible for customer data, encrypting that data, and protecting it through network firewalls and backups


abstracted services
-------------------
- AWS: operates the infra layer, os, and platforms, as well as server-side encryption and data protection
- you are responsible for managing customer data and protectin it through client-side encryption

Source:
- https://aws.amazon.com/compliance/shared-responsibility-model/https://aws.amazon.com/compliance/shared-responsibility-model/