# Identity & Access Management

IAM (Identity and Access Management) is a service provided by Amazon Web Services (AWS) that enables you to securely manage access to your AWS resources. IAM allows you to create and control AWS users, groups, roles, and their permissions, allowing you to manage who can access specific resources and what actions they can perform.

When we first create an AWS account, it has complete access to all AWS services. This identity is called the AWS account root user.

IAM allows you to implement the principle of least privilege, where users are granted only the permissions necessary to perform their specific tasks. This helps ensure that your AWS resources are secure and access is tightly controlled.


**Here are some key points about IAM:**

**Users**: IAM allows you to create individual IAM users within your AWS account. Each user is assigned unique credentials (username and password or access keys) and can have specific permissions and policies associated with them.

**Groups**: IAM lets you organize users into logical groups. By creating groups, you can assign common permissions and policies to a set of users, making it easier to manage their access.

**Roles**: IAM roles are similar to users, but they are not associated with a specific person or identity. Instead, roles are assumed by trusted entities, such as AWS services or applications running on EC2 instances.

**Policies**: IAM policies are JSON documents that define the permissions for users, groups, and roles. Policies specify the actions that are allowed or denied on specific resources and can be fine-tuned to provide granular control over access. Policies can be attached at the user, group, or role level.

**Access Keys**: IAM provides access keys, consisting of an access key ID and a secret access key, which are used for programmatic access to AWS resources via the AWS API.


**IAM - Features**

**• Shared access to the AWS account**: The main feature of IAM is that it allows you to create separate usernames and passwords for individual users or resources and delegate access.

**• Multifactor authentication (MFA)**: IAM supports MFA, in which users provide their username and password plus a one-time password from their phone a randomly generated number used as an additional authentication factor.

**• Identity Federation**: If the user is already authenticated, such as through a Facebook or Google account, IAM can be made to trust that authentication method and then allow access based on it.

**• Free to use**: There is no additional charge for IAM security. There is no additional charge for creating additional users, groups or policies.

**• Password policy**: The IAM password policy allows you to reset a password or rotate passwords remotely.

**• Granular permissions**: Each user can be granted with different set granular permissions as required to perform their job.


**Types of Account in AWS**

1. Root User<br/>
2. IAM User<br/>


**Root User**

The root account is created when you first sign up for AWS. It has complete administrative access to all AWS services and resources in the account. The root account has full control over billing, access management, and all aspects of the AWS environment. 

**IAM User**

IAM user represents the person or service who uses the access to interact with AWS.

IAM user starts with no permissions and is not authorized to perform any AWS actions on any AWS resources and should be granted permissions as per the job function requirement.

Each IAM user is associated with one and only one AWS account.

Number of ways we can login to AWS account<br/>
Console/Graphical User Interface (GUI)
Command Line Interface




