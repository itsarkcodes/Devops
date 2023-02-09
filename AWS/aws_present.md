# Let's Explore the Cloud with a smile :)

## What is S3?
The **Amazon Simple Storage Service**, S3, is an object-based storage system. Now, in the next lesson

![image](https://user-images.githubusercontent.com/87442305/217566275-c23aa387-4a19-4d74-8e09-6c2bcae19948.png)

• You can store any type of file in S3

• Files can be anywhere from 0 bytes to 5 TB

• There is unlimited storage available

• S3 is a universal namespace so bucket names must beunique globally

• However, you create your buckets within a REGION

• It is a best practice to create buckets in regions that are physically closest to your users to reduce latency

• There is no hierarchy for objects within a bucket

• Delivers strong read-after-write consistency

# Buckets, Folders, and Objects

![image](https://user-images.githubusercontent.com/87442305/217568554-be678eb2-e8f0-4a72-a64f-70c62fb2de36.png)

# Accessing Amazon S3

![image](https://user-images.githubusercontent.com/87442305/217571347-a503396a-d42c-4384-85b2-7d6efc078b56.png)

# Create Amazon S3 Bucket

## IAM Policies
• IAM Policies are identity-based policies

• Specify what actions are allowed on what AWS resources

![image](https://user-images.githubusercontent.com/87442305/217572263-b2e10a07-c31b-4468-800c-4d623166092b.png)

## Bucket Policies

• Bucket Policies are resource-based policies

• Can only be attached to Amazon S3 buckets

• Also use the AWS access policy language

![image](https://user-images.githubusercontent.com/87442305/217572724-c19d2321-d6cd-4060-8177-c0d4c0c49353.png)

> EG:

> ![image](https://user-images.githubusercontent.com/87442305/217576545-df4dd3da-f127-416c-ae8c-efe8c5e233fc.png)


# Amazon DynamoDB

• Fully managed NoSQL database service

• Key/value store and document store

• It is a non-relational, key-value type of database

• Fully serverless service

• Push button scaling

![image](https://user-images.githubusercontent.com/87442305/217573975-d6d19b99-b8a4-432c-94c1-9be96227f7c9.png)

### DynamoDB is made up of:
  - Tables, Items, Attributes
![image](https://user-images.githubusercontent.com/87442305/217574460-a1a4f6e9-6526-4a53-b637-bd01650c9c6a.png)

## Features and Benefits
![image](https://user-images.githubusercontent.com/87442305/217578776-07fddd0e-b979-4ee4-8754-c183b1d7189c.png)

# Amazon Route53
Amazon Route 53 is a highly available and scalable Domain Name System (DNS) web service.

### But wait! What is a DNS?
![image](https://user-images.githubusercontent.com/87442305/217580560-d450296b-2f5f-440b-9e60-c507d806fcea.png)

### Lets look at Route53

![image](https://user-images.githubusercontent.com/87442305/217584264-519d27b8-45ea-44a0-8ef1-876a902dc252.png)

### How to create a hosted zone and connect to your EC2 instance 

- Access Service and create Hosted Zone
![image](https://user-images.githubusercontent.com/87442305/217587155-6247089b-1cfe-4329-83b0-147e7f5fdda1.png)

- Name the hosted zone (Add your domain name)
![image](https://user-images.githubusercontent.com/87442305/217587571-63239919-4dbe-4b6d-8749-c60ca0017e25.png)

- Hosted Zone 
![image](https://user-images.githubusercontent.com/87442305/217587876-f41e4346-825f-48eb-86c0-77cf014c07ea.png)

- Create a record set
![image](https://user-images.githubusercontent.com/87442305/217588427-13742fc6-bd0e-4f9f-9e13-f6d481f03859.png)

- Fill the details
![image](https://user-images.githubusercontent.com/87442305/217589231-48750305-6d2a-4fe1-8dc5-76966feaa677.png)

### Routing Policies
- Simple: Simple DNS response providing the IP address associated with a name

- Failover: If primary is down (based on health checks), routes to secondary destination

- Geolocation: Uses geographic location you’re in (e.g. Europe) to route you to the closest region

- Geoproximity: Routes you to the closest region within a geographic area

- Latency: Directs you based on the lowest latency route to resources

- Multivalue answer: Returns several IP addresses and functions as a basic load balancer

- Weighted: Uses the relative weights assigned to resources to determine which to route to

### Features of Route53

![image](https://user-images.githubusercontent.com/87442305/217590292-894e7e0e-6112-486f-8733-7fd3dcdb2c85.png)

