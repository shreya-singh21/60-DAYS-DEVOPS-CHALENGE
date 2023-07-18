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
Console/Graphical User Interface (GUI)<br/>
Command Line Interface

**Lets create IAM User**

1. Go to IAM.

2. Create two IAM users. One user will access only EC2 Machines & Second user will access only S3 Buckets.

3. Click on Users

4. Click on Add users

5. Give the user name.

6. 

7. You have select password format type<br/>
   auto generated password<br/>
   custom password

8. click on custom password and enter the password

9. require password reset permission by default it is checked<br/>
   Whenever user will login account at the first time by default they need to change "IAMUserChangePassword"<br/>
   If you don't want to provide the user to chnage password you can uncheck this check box.
   
10. Click on Next: Permissions

11. You will find 3 ways to attach permission<br/>
    Add user to group<br/>
    copy permission from existing user<br/>
    Attach existing policies directly
  
12. Click on Attach existing policies directly

13. Whatever the permission you need to provide user you can seach. Example - You need to give the "EC2 full Access" policy to    particular user. In this person have full access of EC2 service and they can work freely on EC2.

14. Select the policy

15. Click on Next: Tags

16. Click on Next: Review

17. Click on Create user

18. After creating user you can download .CSV file and shared it or you can send email directly to particular user.

19. Now Create Another User and give "S3 Full Access" permission with above same procedure

20. Now we have two user<br/>
    User1 -> EC2 Full Access
    User2 -> S3 Fully Access

21. User can access the AWS with the credentials provided by .CSV file but they have only permission to use those services for which root account has given permission.

22. They can also change the password after first login.

23. Login to user AWS account.

24. Login both account with the IAM credentials.

**Note**- 1. Whatever the IAM user will do it will reflect in root account.<br/>
          For ex- if user1 has created EC2 instance so same EC2 will also reflect in root account.<br/>
          All the billing will be calculated from root user account not from IAM user account.

          2. In IAM account if the person is trying to access the service which they don't have permission will get the error message.


**Groups & Attach Policies**

IAM Group is a collection of users. In IAM group we can add user and attach policies. Whatever policies atatched to group will apply the same policies on users and whenever the user is going to remove automatically permission is going to remove from user.

**Following are some important characteristics of user groups:**

• A user group can contain many users, and a user can belong to multiple user groups.

• User groups can't be nested; they can contain only users, not other user groups.

• There is no default user group that automatically includes all users in the AWS account. If you want to have a user group like that, you must create it and assign each new user to it.


**Let's create IAM group**

1. Go to IAM.

2. Click on user group

3. click on create group.

4. Give the name of group

5. Add user in group

6. Attach policies on group. For ex- S3 Full Access.

7. Now try to login to particular IAM user. User can have the same permission to access the service. User can also access the s3.

8. If you create user2 and add in same group then user2 will have same  access as the group.


**Custom Policies**

Custom policies means we acn create our own policies based on requirement.

1. Go to IAM

2. Click on Policies

3. Click on create policy

4. Now you have to select service. There you will find all aws service. Select IAM.

5. Select Action. What action you want to give to user. For ex- List and Read access<br/>
   The persion can have only list whatever in the IAM service and read it.

6. Go to resource and click on all resources.

7. Click on Next.

8. Click on Review.

9. Give the name of policy.

10. Create Policy.

11. Now create user. Go to attach policy directly and search the policy name which you have created.

12. Now login to particular user and you will find that the user have access to list and read whetever have in the IAM service.


**Password Policy**

We can set a custom password policy on our AWS account to specify complexity requirements and mandatory rotation periods for your IAM users' passwords. The IAM password policy does not apply to the AWS account root user password.

When we configure a custom password policy for your account, we can specify the following conditions:

• Password minimum length: We can specify a minimum of 6 characters and a maximum of 128 characters.

• Password strength: You can select any of the following check boxes to define the strength of your IAM user passwords.

• Require at least one uppercase letter from Latin alphabet (A–Z)

• Require at least one lowercase letter from Latin alphabet (a–z)

• Require at least one number

• Require at least one non alphanumeric character ! @ # $ % ^ & * ( ) _ + - = [ ] { } | '

• Password Expiration: Require users to change the password after some days

• Allow All IAM users to change their own password

• Prevent Password Reuse: You can prevent IAM users from reusing a specified number of previous passwords. You can specify a minimum number of 1 and a maximum number of 24 previous passwords that can't be repeated.


1. Go to IAM.

2. Go to account settings

3. You will find default password policy. Click on Edit.

4. In Password policy click on custom

5. Now whichever the policy you want to use just check the checkbox.

6. Save changes.
