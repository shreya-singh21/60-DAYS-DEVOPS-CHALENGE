# Day 8: Identity & Access Management
"Identity & Access Management (IAM) is a service provided by Amazon Web Services (AWS) that helps you control and manage access to your AWS resources securely. When you first create an AWS account, you have full access to all AWS services, which is called the AWS account root user.

However, in a real-world scenario, an organization or a team may use the AWS account, and they might not want to give full access to every team member or employee. Instead, they want to provide specific permissions to each person based on their tasks. This is where IAM comes in handy.

With IAM, you can create individual IAM users for each team member or employee, and each IAM user has limited access to AWS services based on what they need to do their job. For example, you can create an IAM user and give them access only to the Amazon EC2 service to manage virtual machines, or you can assign another IAM user access to Amazon S3 to handle file storage.

By implementing IAM, organizations can follow the principle of least privilege, granting only the necessary permissions to each IAM user, ensuring that AWS resources are secure and access is tightly controlled."

## Here are some key points about IAM:

**1.Users**: IAM allows you to create individual IAM users within your AWS account. Each user is assigned unique credentials (username and password or access keys) and can have specific permissions and policies associated with them.

**2.Groups**: IAM lets you organize users into logical groups. By creating groups, you can assign common permissions and policies to a set of users, making it easier to manage their access.

**3.Roles**: IAM roles are similar to users, but they are not associated with a specific person or identity. Instead, roles are assumed by trusted entities, such as AWS services or applications running on EC2 instances.

**4.Policies**: IAM policies are JSON documents that define the permissions for users, groups, and roles. Policies specify the actions that are allowed or denied on specific resources and can be fine-tuned to provide granular control over access. Policies can be attached at the user, group, or role level.

**5.Access Keys**: IAM provides access keys, consisting of an access key ID and a secret access key, which are used for programmatic access to AWS resources via the AWS API.


## IAM - FEATURES

**• Shared access to the AWS account**: The main feature of IAM is that it allows you to create separate usernames and passwords for individual users or resources and delegate access.

**• Multifactor authentication (MFA)**: IAM supports MFA, in which users provide their username and password plus a one-time password from their phone a randomly generated number used as an additional authentication factor.

**• Identity Federation**: If the user is already authenticated, such as through a Facebook or Google account, IAM can be made to trust that authentication method and then allow access based on it.

**• Free to use**: There is no additional charge for IAM security. There is no additional charge for creating additional users, groups or policies.

**• Password policy**: The IAM password policy allows you to reset a password or rotate passwords remotely.

**• Granular permissions**: Each user can be granted with different set granular permissions as required to perform their job.


## TYPES OF ACCOUNT IN AWS

1. Root User<br/>
2. IAM User<br/>


**ROOT USER**

The root account is created when you first sign up for AWS. It has complete administrative access to all AWS services and resources in the account. The root account has full control over billing, access management, and all aspects of the AWS environment. 

**IAM USER**

IAM user represents the person or service who uses the access to interact with AWS.

IAM user starts with no permissions and is not authorized to perform any AWS actions on any AWS resources and should be granted permissions as per the job function requirement.

Each IAM user is associated with one and only one AWS account.

Number of ways we can login to AWS account<br/>
Console/Graphical User Interface (GUI)<br/>
Command Line Interface

## Lets create IAM User

1. Go to IAM.

2. Create two IAM users. One user will access only EC2 Machines & Second user will access only S3 Buckets.

3. Click on Users

4. Click on Add users

5. Give the user name.

6. Click on enable console access<br/>
  
7. You will get two option<br/>
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


## GROUPS & ATTACH POLICIES

IAM Group is a collection of  IAM users. In IAM group we can add user and attach policies. Whatever policies atatched to group will apply the same policies on users and whenever the user is going to remove automatically permission is going to remove from user.

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


## CUSTOM POLICIES

In AWS Identity and Access Management (IAM), Custom Policies allow you to create your own set of rules and permissions to control access to AWS resources based on your specific requirements. These policies are custom-made and tailored to meet the needs of your organization or individual users.
**Example**
Let's say you have an AWS account with multiple IAM users, each with different roles and responsibilities. One of the users, John, is responsible for managing Amazon S3 buckets, while another user, Sarah, needs access to EC2 instances for testing purposes.

To give John and Sarah the necessary permissions without granting them full access to the entire AWS environment, you can create Custom Policies. For John, you would create a policy that grants him read, write, and delete access to specific S3 buckets. For Sarah, you would create a policy that allows her to start, stop, and terminate EC2 instances.

By applying these Custom Policies, John and Sarah will have the precise access they need to perform their tasks, while other resources in the AWS account remain secure.

Custom Policies provide you with fine-grained control over access to AWS resources, allowing you to enforce the principle of least privilege. This principle ensures that users have only the permissions required for their specific tasks, minimizing potential security risks and enhancing the overall security of your AWS environment.

**Steps**

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


## PASSWORD POLICIES

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


## MULTI-FACTOR AUTHENTICATION

MFA, or Multi-Factor Authentication, is a security feature provided by AWS IAM (Identity and Access Management). It adds an extra layer of protection to user accounts by requiring users to provide additional authentication factors, in addition to their username and password, when signing in to AWS services.

**Here's how MFA works in AWS IAM:**

**1.Enabling MFA**: To use MFA, you first need to enable it for your IAM user account. This involves associating a virtual or hardware MFA device with your account. A virtual MFA device can be an app on your smartphone, while a hardware MFA device is a physical device that generates authentication codes.

**2.Authentication Factors**: Once MFA is enabled, when you sign in to your IAM user account, you'll be prompted to provide two authentication factors:<br/>
**Username and password**: The first factor is your regular IAM user credentials, including your username and password.<br/>
**MFA code**: The second factor is a unique code generated by your MFA device. For virtual MFA devices, this code is typically displayed within an authentication app, while for hardware devices, you would press a button to generate the code.

**3.Increased Security**: By requiring two factors for authentication, MFA significantly enhances the security of your AWS account. Even if an unauthorized person obtains your username and password, they would still need access to your MFA device to generate the correct authentication code.

**4.MFA for Privileged Actions**: In AWS, you can also enforce MFA for specific actions that require elevated privileges, such as modifying security settings or accessing sensitive data. This ensures that these actions are further protected by the MFA authentication process, adding an extra layer of security to critical operations.


**MFA - DEVICES OPTIONS**

AWS provides two options for MFA devices:

**1.Virtual MFA Device**: A virtual MFA device is a software application that runs on your smartphone, tablet, or other mobile devices. It generates the authentication codes needed for MFA. You can use various authenticator apps, such as Google Authenticator, Microsoft Authenticator, or Authy, to set up a virtual MFA device.

**2.Hardware MFA Device**: A hardware MFA device is a physical device that generates MFA authentication codes. It is a separate device, often in the form of a keychain or small token, that you carry with you. The device typically has a button that you press to generate the authentication code. Examples of hardware MFA devices include YubiKey and RSA SecurID.


### To use Multi-Factor Authentication (MFA) in AWS, you can follow these steps:

**MFA – ROOT USER**

1. Download the mobile App (Authy)

2. Go to Security Credentials

3. Go to Multi Factor Authentication

4. Click on Activate MFA

5. Select the Device (Virtual MFA Device)

6. Click on Continue

7. Go to Multi Factor Authentication

8. Click on Activate MFA

9. Give the device name.

10. Select MFA<br/>
    Authenticator App

11. Click on Continue

12. Click on Show QR Code

13. Click on plus button in mobile App

14. Enter Backup Password in mobile App

15. Click on Scan code from mobile App

16. Click on Enable Password in mobile App

17. Click on Save

18. System will generate the Code in mobile App

19. Enter the code in AWS

20. After few Seconds new password will generate in mobile App

21. Enter the Second Code

22. Click on Assign MFA

23. Now logout user and try to Login with AWS Account

24. When you enter password it will ask MFA code.


**MFA – IAM USER**

1. Create IAM User

2. Click on username

3. Go to Security Credentials

4. Click on Manage for MFA Device

5. Select the Type & Click on Continue

6. Click on Show QR Code

7. Click on Add Account in mobile App

8. Scan QR Code from mobile App

9. Save on save in mobile APP

10. Password will generate in mobile App

11. Click on Assign MFA

12. Check our IAM User

13. Try to login IAM user


## COMMAND LINE INTERFACE

AWS CLI (Command Line Interface) is a unified tool provided by Amazon Web Services (AWS) that allows you to interact with various AWS services through a command-line interface. It enables you to manage and automate your AWS resources using scripts or commands from your local machine.


**CLI - WINDOWS**

1. Enable Access Key

2. Go to My Security Credentials

3. Go to Access Keys

4. Click on Create New Access Key

5. Note down the access key and secret acess key. Also you can download .CSV file

6. Now login with the command prompt
   Download and Install  AWS CLI

7. After downloading and installing AWS CLI 

8. Open command prompt

9. Write "aws configure"

10. Enter our AWS Access Key

11. Enter Secret Access Key

12. Enter our default region name for ex- ap-south-1(mumbai)

13. Enter default output format - text

14. Create one S3 Bucket with Consol/GUI

15. Now use command line to list the s3 bucket.<br/>
    aws s3 ls

16. Create Bucket Using CLI<br/>
    aws s3 mb s3://<Bucket_Name>

**Note**- Whenever we create bucket with CLI it gets public access.

17. Upload object using CLI<br/>
    aws s3 cp <Object_name with extension> s3://<Bucket_name>/<Object_name with extension>

**Note**- Whenever we are uploading object with CLI by default object are getting Public Access.


**CLI - LINUX**

1. For Linux Machine we need to create one Linux EC2 Machine.Whenever we are creating Linux machine by default it is installed with CLI.

2. Connect linux EC2 machine

3. Switch User<br/>
   sudo su -

4. Update repository<br/>
   yum update -y

5. Generate access key and secret key from GUI

6. From CLI connect aws
   
7. Configure AWS<br/>
   aws configure

8. Enter Access Key<br/>

9. Enter Secret Access Key<br/>

10. Enter default region name- ap-south-1<br/>

11. Enter default output format- text<br/>

12. Create IAM user using CLI<br/>
    aws iam create-user --user-name <User_Name><br/>
    for ex- aws iam create-user --user-name user6

13. Now check in AWS GUI.

14. Create IAM Group<br/>
    aws iam create-group --group-name <group_name>

15. Check in AWS GUI.


**CLI – WINDOWS (IAM USER)**

Creating IAM user with CLI

1. Create IAM user

2. Go to IAM

3. Give user name

4. Click on enable console access<br/>
  
5. You will get two option<br/>
   auto generated password<br/>
   custom password

6. Click on autogenerated password

7. Click on Next: Permissions

8. You will find 3 ways to attach permission<br/>
    Add user to group<br/>
    copy permission from existing user<br/>
    Attach existing policies directly
  
9. Click on Attach existing policies directly

10. Search AmazonEC2FullAccess

11. Craete user

12. Generate Access key

13. Go to User. Go to security credentials

14. Create access key

15. Select comamnd Line Interface(CLI)

16. Open command prompt

17. Use aws configure

18. Enter Access Key<br/>

19. Enter Secret Access Key<br/>

20. Enter default region name- ap-south-1<br/>

21. Enter default output format- text<br/>

**Note** - Previously we have seen CLI commands for IAM, S3. Now this time will see for EC2.

22. To Create EC2 machine we need some details

23. Note down AMI Number<br/>
    Go to EC2 Service<br/>
    Go to AMI catalog<br/>
    Search "Microsoft Windows Server 2022 Core Base"<br/>
    Note down the AMI ID

24. Note down Key Pair Name

25. Note Down Security Group ID

26. Create EC2 Machine<br/>
    aws ec2 run-instances --image-id <enterAmiID> --count 1 --instance-type t2.micro --key-name <MyKeyPair> --securitygroup-ids <enterSecurityGroupId>

27. Check in AWS console.

28. Describe Instance to get all details<br/>
    aws ec2 describe-instances --instance-ids <Instance_Id>

29. Terminate the instance <br/>
    aws ec2 terminate-instances --instance-ids <Instance_Id>


## IAM- ROLES

In AWS IAM (Identity and Access Management), a role is an entity that defines a set of permissions and policies. Roles are used to grant temporary access to AWS resources to entities such as IAM users, AWS services, or external identities (e.g., federated users).

Here are some key points about roles in IAM:

**1.Purpose**: Roles are designed to delegate permissions and access to AWS resources securely. Instead of attaching policies directly to individual IAM users, roles provide a way to assign permissions to different entities based on specific use cases or requirements.

**2.Cross-account Access**: Roles can be used to grant access across AWS accounts. For example, a parent AWS account can create a role with specific permissions and allow another AWS account (child account) to assume that role and access resources in the parent account.

**3.Service Roles**: Roles are also used to enable AWS services to access other AWS resources securely. These are called service roles or service-linked roles. AWS services, such as AWS Lambda or Amazon EC2, assume these roles to perform specific actions on your behalf.

**4.Temporary Credentials**: Roles can provide temporary security credentials that can be assumed by trusted entities. This is useful for scenarios where access needs to be granted for a limited time, such as when using AWS STS (Security Token Service) to assume a role with time-limited credentials.

1. In IAM, got to roles

2. Create Roles

3. Choose AWS Service

4. Select EC2 Use Case

5. Click on Next

6. select policy which you need to select to EC2 Service.

7. Give role name

8. Create role

9. Create Linux EC2 Machine 

10. Attach Role to the EC2 Machine

11. Go to Action -> Security-> IAM role

12. Modify IAM Role

13. Update IAM role

14. We have created the role and linked that particular role.

15. Now we have to use it

16. Connect to linux EC2 machine using putty

17. Create IAM user
    aws iam create-user --user-name <User_Name><br/>
    AS we have nota ttached the IAM role. We will get an error.

18. Create the S3 Bucket
    aws s3 mb s3://<Bucket_Name>


**CONNECT S3 BUCKET USING WINSCP**

1. Create S3 Bucket

2. Create IAM user

3. Give the Full permission of S3

4. Note down the Access Key ID & Secret access key

5. Open WINSCP

6. Change File Protocol to Amazon S3

7. Enter access key ID and secret key

8. Click on Login

9. Open the bucket

10. Transfer file to the bucket

11. Check Console


**ENABLE S3 MFA**

1. Enable MFA for our account<br/>
   Go to security credentials <br/>
   Assign MFA<br/>
   Click on OQ Code<br/>
   Give MFA code1 and MFA code2

2. Logout user and login again

3. Go to S3 service

4. Create S3 Bucket

5. Enable Versioning

6. Open Comamnd prompt

7. connect to aws by aws configure command

8. Generate the access key & secret key id

9. Enter Access Key<br/>

10. Enter Secret Access Key<br/>

11. Enter default region name- ap-south-1<br/>

12. Enter default output format- text<br/>

13. Enable MFA for S3<br/>
aws s3api put-bucket-versioning --bucket <bucket_name> --versioning-configuration Status=Enabled,MFADelete=Enabled --mfa "<MFA_Serial_Number> <MFA_Code>

14. Now check the s3 bucket

15. Upload object in S3 bucket

16. Click on show versions

17. Select the object & click on delete

18. Delete the object using CLI
aws s3api delete-object --bucket s3bucketmfa --key <Object_Key_Name> --mfa "<MFA_Serial_Number><MFA_Code>

19. Now check the bucket

20. Disable S3 MFA
aws s3api put-bucket-versioning --bucket <Bucket_Name> --versioning-configuration Status=Enabled,MFADelete=Disabled --mfa "<MFA_Serial_Number> <MFA_Code>“

21. Check the S3 Bucket









    






