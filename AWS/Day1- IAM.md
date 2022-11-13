AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS resources. You use IAM to control who is authenticated (signed in) and authorized (has permissions) to use resources.

**IAM settings are used globally. You dont have to select any region**

**Groups:-** Way to organise users. Then we can apply permission to users, it will be applied to all users

**Policy:**- permissions which are then applied to a group. Defines what the people can access or do in a group

**Identity Policies:-** Identity-based policies can be applied to users, groups, and roles

# IAM Users:
**Root Users** :- The root user has full permissions. It’s a best practice to avoid using the root user account + enable MFA

**Individual Users:-** Upto 5000 users can be created (no permissions by default)

# IAM Groups
An IAM user group is a collection of IAM users. User groups let you apply permissions to users using policy
![image](https://user-images.githubusercontent.com/87442305/201469736-962e71de-607e-4482-84a7-02d444f877a2.png) 

Here are some important characteristics of user groups:
-   A user group can contain many users, and a user can belong to multiple user groups.
-   User groups can't be nested; they can contain only users, not other user groups.
-   There is no default user group that automatically includes all users in the AWS account. If you want to have a user group like that, you must create it and assign each new user to it.
-  10 Members Max in each group

# IAM Roles

- IAM roles is an IAM identity that has specific permission
- Roles are assumed by users, application, and services
![image](https://user-images.githubusercontent.com/87442305/201469928-abbc5874-cb0d-4b37-9912-0d4aead0c23e.png)

# IAM Policies
- Policies are documents that define permissions and are written in JSON

**Identity-based Policies** :-
Assigned to users, groups and roles.

![image](https://user-images.githubusercontent.com/87442305/201469830-5fce202b-5eee-49ac-8eb6-870cb449803b.png)
> All permissions are implicitly deined by default

**Resource Based Policies** :-
applies to specific resources such as s3 buckets or DynamoDB tables
![image](https://user-images.githubusercontent.com/87442305/201469888-4b8902c7-3981-41d7-a974-15950ebef478.png)

# IAM Security Token Service STS
AWS provides AWS Security Token Service (AWS STS) as a web service that enables you to request **temporary, limited-privilege credentials** for IAM users or federated users (Users outside AWS)

An STS will return
> Access Key ID  
> Secret Access Key  
> Session Token  
> Expiration  

![image](https://user-images.githubusercontent.com/87442305/201470804-323e5b3a-cbf0-4729-8a59-b3089c218c1f.png)

# Identity-Based IAM Policies
Identity-based policies are attached to an IAM user, group, or role. These policies let you specify what that identity can do (its permissions).  
They are JSON based permissions policy document

- Eg: you can attach the policy to the IAM user named John, stating that he is allowed to perform the Amazon EC2 RunInstances action. The policy could further state that John is allowed to get items from an Amazon DynamoDB table named MyCompany

  ## 1.Inline Policy
   - An inline policy is a policy that's embedded in an IAM identity (a user, group, or role).
   - If you delete a user, You delete the policy along with it 
   - You cannot share the policy
   - Inline policies are useful if you want to maintain a strict one-to-one relationship between a policy and the identity to which it is applied
   - **Eg:** Inline policies are useful if you want to maintain a strict one-to-one relationship between a policy and the identity to which it is applied. For example, you want to be sure that the permissions in a policy are not inadvertently assigned to an identity other than the one they're intended for.

  ## 2. Managed Policy
    **1. AWS Managed policy**     
      - This policies are created and managed by AWS  
      - It is a standalone policy means, that the policy has its own Amazon Resource Name (ARN) that includes the policy name.   
      - For example, arn:aws:iam::aws:policy/IAMReadOnlyAccess is an AWS managed policy. 
      ![image](https://user-images.githubusercontent.com/87442305/201508937-7597e4ab-52b3-4361-b71f-046bee4f0e09.png)
      
     **2. Customer Managed Policy**       
      - This policy is created and administrated by the customer itself      
       ![image](https://user-images.githubusercontent.com/87442305/201509285-e9c2f3ed-9ff0-4f55-a6b5-3c541e776768.png)

# Resource Based Policy
Resource based policies are JSON Policy documents that you attach to a resource such as an Amazon S3 Bucket

![image](https://user-images.githubusercontent.com/87442305/201509557-bce78728-4375-4256-b835-9f8fade14fa9.png)

## IAM ROLE
![image](https://user-images.githubusercontent.com/87442305/201509622-8d55d955-0852-4f67-9438-85a1d1f67b77.png)

# IAM Policy Structure
![image](https://user-images.githubusercontent.com/87442305/201514444-a63dc6f2-e0c7-4c01-98b2-cec127bf3958.png)

Example 1:    
![image](https://user-images.githubusercontent.com/87442305/201514479-5c2f51bc-87a8-43c3-9315-17b922efa9a7.png) 

Example 2:     
![image](https://user-images.githubusercontent.com/87442305/201515563-d1ff5b66-e50c-42a9-ad05-92a602781744.png)


# Best Practises
• Lock away your AWS account root user access keys   
• Create individual IAM users           
• Use groups to assign permissions to IAM users       
• Grant least privilege          
• Get started using permissions with AWS managed policies              
• Use customer managed policies instead of inline policies          
• Use access levels to review IAM permissions             
• Configure a strong password policy for your users             
• Enable MFA           
• Use roles for applications that run on Amazon EC2 instances            
• Use roles to delegate permissions          
• Do not share access keys           
• Rotate credentials regularly          
• Remove unnecessary credentials           
• Use policy conditions for extra security            
• Monitor activity in your AWS account               





