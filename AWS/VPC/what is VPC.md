# What is VPC
- A VPC in AWS is like having your own private network in the cloud. It allows you to create and manage your own isolated virtual network environment
- **_Max 5 VPC_** Can be created and **_200 subnets_** in 1 VPC. i.e total 1000 subnets
- We can attach max 5 Elastic IP (can be extended)
- Once we create a VPC, DHCP (Dynamic Host Configuration Protocol), NACL (Network Access Control List) and Security Group will be automatically created (See in Labs)
- VPC is configured on region and not on AZ 

## Example
- To understand this concept with a real-world example, let's imagine you have a big office building with different departments, such as HR, Finance, and IT. Each department has its own dedicated area with specific resources and access rules.
- Now, think of the entire office building as the AWS cloud, and each department as a separate VPC. Each VPC (department) has its own set of resources like servers, databases, and storage, and they are completely isolated from each other.
- Just like in the real world, you can control who has access to each department in the office building. Similarly, in AWS, you can control the access to your VPCs by configuring security rules, called security groups and network access control lists (ACLs), to allow or deny incoming and outgoing network traffic.
- By using VPCs, you can create multiple virtual networks within the AWS cloud and securely connect them to your on-premises infrastructure, if needed. This allows you to have different applications and services running in separate VPCs, providing an extra layer of security and isolation.
