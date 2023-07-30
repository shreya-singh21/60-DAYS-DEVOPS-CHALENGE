# Domain Name System (DNS)

The Domain Name System (DNS) is like a phonebook for the internet. It helps us find websites using easy-to-remember domain names like "www.example.com" instead of complicated numerical IP addresses like "192.168.1.1." DNS translates domain names into IP addresses, which are essential for data routing.

## How DNS Works?

1. **Request**: When you type a domain name into your web browser, your computer sends a request to the DNS server, asking for the IP address associated with that domain.

2. **Lookup**: The DNS server checks its records and finds the corresponding IP address for the domain name you entered.

3. **Response**: Once the IP address is found, your computer can directly request the website's content from the web server at that specific address.

## Example:

Suppose you want to visit "www.example.com." Your computer asks the DNS server for its IP address. Let's say the DNS server replies with "192.0.2.1."

Now, armed with the IP address, your computer sends a request to the web server at "192.0.2.1," asking for the website's content.

## Importance of DNS:

1. **Human-Friendly**: DNS makes the internet user-friendly, allowing us to use simple domain names instead of complex IP addresses.

2. **Global Connectivity**: DNS enables seamless communication between devices worldwide, regardless of their physical location.

3. **Scalability**: DNS can handle millions of domain names and devices, making it scalable for the growing digital world.

4. **Redundancy and Load Balancing**: DNS distributes website traffic across multiple servers, ensuring faster response times and better performance.

5. **Service Discovery**: DNS is used for service discovery, allowing devices to find and communicate with other services on the internet.

In summary, DNS is a fundamental system that underpins the internet's functionality, making it easier for us to access websites, send emails, and connect with others across the globe.

## Route 53 - AWS DNS Service
DNS Service in AWS is called route 53. We can register our domain name in route 53, godaddy, freenon etc.

Route 53 is Amazon Web Services' (AWS) DNS service that allows us to manage domain names and their DNS settings. It serves as a phonebook for the internet, translating human-friendly domain names into numerical IP addresses.

## Routing Policies in Route 53

Route 53 offers six routing policies for directing traffic to different resources:

1. **Simple Routing Policy**: Distributes traffic evenly across multiple resources linked to a single domain name.

2. **Latency Routing Policy**: Routes traffic to the server with the lowest latency, providing the quickest response time for users.

3. **Failover Routing Policy**: Creates a backup resource that takes over when the primary resource fails, ensuring high availability.

4. **Weighted Routing Policy**: Distributes traffic based on assigned weights, allowing us to control the proportion of traffic to different resources.

5. **Geolocation Routing Policy**: Directs traffic to specific resources based on the geographic location of the user.

6. **Multivalue Routing Policy**: Returns multiple IP addresses for a domain name, randomly selecting one for each user's query, which is useful for load balancing and redundancy.

In summary, Route 53 is a powerful DNS service that enables us to register and manage our domain names and control how traffic is routed to our resources.

## Simple Routing Policy in AWS Route 53

The Simple Routing Policy is the default routing policy provided by AWS Route 53. It is commonly used when we have a single resource in a specific region that serves a particular function for our domain.

**How It Works**

Imagine you have a website hosted on an EC2 instance in the US-West (Oregon) region with the IP address "203.0.113.10". When a user enters your domain name (e.g., www.example.com) in their web browser, their computer sends a DNS query to AWS Route 53 to resolve the domain name to an IP address.

With the Simple Routing Policy, Route 53 looks at the resource record set associated with the domain (e.g., the "A" record), which contains the IP address "203.0.113.10" for your website. Route 53 then responds to the DNS query with this IP address. The user's web browser can now use this IP address to connect to your website hosted in the US-West (Oregon) region.

#### Steps to Create Simple Routing Policy in AWS Route 53 with an AWS Domain

To create a simple routing policy in AWS Route 53, you will need a domain name. Domain names serve as user-friendly addresses for accessing websites or applications hosted on the internet. You have two options to obtain a domain name: you can either purchase it directly from AWS or from another domain registrar outside of AWS.

If you choose to buy the domain from AWS, the steps for creating the simple routing policy will be different compared to when you use a domain from an external registrar. Let's first understand the process of setting up a simple routing policy with an AWS domain name, and later we will explore the steps for other domain registrars.

**Steps for Setting Up Simple Routing Policy with an AWS Domain Name**

1. Go to the AWS Management Console and navigate to the Route 53 dashboard.
2. Click on "Registered Domains" to buy a domain name according to your budget and requirements. You can purchase a domain name directly from AWS or from other domain registrars.
3. After creating the domain, set up your web server or application. For this example, let's create one or two EC2 instances to host your website or application.
4. Next, create a target group and add EC2 instances.
5. Now, create an Application Load Balancer in the EC2 service and attach the target group to this load balancer. The load balancer will distribute incoming traffic across the EC2 instances in the target group.
6. Once the load balancer is successfully created, copy its DNS name (endpoint) provided by AWS.
7. Paste the load balancer's DNS name into your web browser and check if it displays your website or application. This step ensures that the load balancer is working correctly and forwarding traffic to the EC2 instances.
8. Go back to the Route 53 dashboard and click on "Hosted Zones."
9. Click on the domain name that you created earlier.
10. Click on "Create Record" to add a new record set for your domain.
11. Enter "www" as the Record Name to create a subdomain for your website (e.g., www.example.com).
12. For the routing policy, choose "Simple Routing Policy."
13. Click on "Alias," and select your Application Load Balancer from the dropdown list.
14. Choose the region where your load balancer is created (e.g., Mumbai region) and select the load balancer from the list.
15. Finally, click on "Create Records" to create the simple routing policy for your domain.

Now, when users enter your domain name (e.g., www.example.com) in their web browser, AWS Route 53 will route the traffic to your Application Load Balancer, which, in turn, will distribute the traffic across the EC2 instances in the target group. This ensures high availability and fault tolerance for your web application.


**Important Considerations**

- The Simple Routing Policy is best suited for scenarios where you have a single resource, such as a website, hosted in a specific region to handle a particular function for your domain.
- If you have multiple resources in different regions and want to route traffic based on latency, geographic location, or other criteria, consider using other routing policies available in Route 53.

In summary, the Simple Routing Policy is an easy and straightforward way to route traffic to a single resource in a specific region for your domain in AWS Route 53.


## Weighted Routing Policy

The Weighted Routing Policy in AWS Route 53 allows you to divide website traffic between different resources or regions based on specific percentages that you assign. It's like splitting incoming visitors to your website into different groups, and each group is sent to a different location based on the weight you set.

**How It Works:**

Imagine you have two regions, "AP South 1" and "AP East 1," and you want to distribute traffic between them. With the Weighted Routing Policy, you can configure the percentages for each region. For example:

- 60% of website visitors go to servers in "AP South 1."
- 40% of website visitors go to servers in "AP East 1."

**Example:**

Let's say you have an online store, and during a special promotion, you expect a high volume of traffic. You want to ensure both "AP South 1" and "AP East 1" regions handle the load efficiently. By using the Weighted Routing Policy, you can direct more visitors to "AP South 1" to handle the majority of the traffic while still sending some traffic to "AP East 1."

This way, you can control the distribution of traffic and ensure both regions are utilized effectively to provide a smooth experience for your website visitors.

#### Steps to Create Weighted Routing Policy in AWS Route 53 with an AWS Domain

To create a weighted routing policy in AWS Route 53 with an AWS domain, we can follow the same steps as we did for the simple routing policy. However, there's an additional step: we'll need to create a new Application Load Balancer with an EC2 instance in the new region where we want to distribute traffic.

Once we have the new load balancer set up, we can proceed to add records in Route 53. When selecting the routing policy, choose "Weighted Routing Policy," and then specify the weight for each load balancer. This weight determines the proportion of traffic that will be directed to each region, allowing you to control the distribution based on your desired percentages.

Let's say we have two regions, Mumbai and Sydney, and we want to distribute incoming traffic with a weight of 60% to the Mumbai region and 40% to the Sydney region. Here's how we can do it:

1. Go to the AWS Management Console and navigate to the Route 53 dashboard.
2. Click on "Hosted Zones" and select your domain name.
3. Click on "Create Record" to add a new record set for your domain.
4. Enter a unique name for the record (e.g., "www").
5. For the routing policy, choose "Weighted Routing Policy."
6. Click on "Alias" and select the Application Load Balancer for the Mumbai region.
7. Choose the region where your Mumbai load balancer is created and select the load balancer from the list.
8. Enter the weight as 60 to assign 60% of the traffic to the Mumbai region.
9. Check the option to evaluate target health.
10. Enter a unique record ID for this record.
11. Click on "Add Another Record" to add another record for the Sydney region.
12. Repeat steps 4 to 9, but this time select the Application Load Balancer for the Sydney region and give it a weight of 40%.
13. Enter a unique record ID for this record as well.
14. Click on "Create Records" to create the weighted routing policy for your domain.

Now, when users enter your domain name (e.g., www.example.com) in their web browser, AWS Route 53 will distribute the incoming traffic based on the weights you specified. 60% of the traffic will be directed to the resources in the Mumbai region, and 40% will be sent to the resources in the Sydney region. 

With the Weighted Routing Policy set up, Route 53 will automatically distribute incoming traffic between the specified regions based on the assigned weights. This allows you to balance traffic load and ensure high availability and performance across your resources.


## Latency-Based Routing Policy

The Latency-Based Routing Policy in AWS Route 53 helps ensure that your website visitors are directed to the AWS region that provides the lowest network latency or fastest response time. It's like guiding your users to the server location that can deliver the website content with the least delay.

**How It Works:**

When a user tries to access your website, AWS Route 53 measures the network latency or the time it takes for data to travel between the user's location and the different AWS regions where your website is hosted. It then directs the user to the AWS region with the lowest latency, which should offer the quickest response time.

**Example:**

Let's say you have your website hosted in two AWS regions: Mumbai and Sydney, and you want to direct traffic to the region with the lowest latency for users in each respective region.

**Steps to Implement Latency-Based Routing Policy in AWS Route 53:**

1. Go to the AWS Management Console and navigate to the Route 53 dashboard.
2. Click on "Hosted Zones" and select your domain name.
3. Click on "Create Record" to add a new record set for your domain.
4. Enter a unique name for the record (e.g., "www").
5. For the routing policy, choose "Latency Routing Policy."
6. Click on "Alias" and select the Application Load Balancer for the Mumbai region.
7. Choose the region where your Mumbai load balancer is created and select the load balancer from the list.
8. Select "Latency" as the route policy for the Mumbai region.
9. Uncheck the option to evaluate target health (since latency is based on network performance, not target health).
10. Enter a unique record ID for this record.
11. Click on "Add Another Record" to add another record for the Sydney region.
12. Repeat steps 4 to 9, but this time select the Application Load Balancer for the Sydney region.
13. Choose the region where your Sydney load balancer is created and select the load balancer from the list.
14. Select "Latency" as the route policy for the Sydney region.
15. Uncheck the option to evaluate target health.
16. Enter a unique record ID for this record as well.
17. Click on "Create Records" to create the latency routing policy for your domain.

Now, when users enter your domain name (e.g., www.example.com) in their web browser, AWS Route 53 will route the traffic to the region with the lowest latency for each user. This ensures that users are directed to the region that will provide them with the best performance and response time.

## Failover Routing Policy

The Failover Routing Policy in AWS Route 53 enables active-passive failover configuration, where one resource handles all the traffic when it's available, and another resource takes over when the first one becomes unavailable. It's like having a backup plan to ensure high availability and resilience for your application.

**How It Works:**

With the Failover Routing Policy, you set up two resources (for example, two different AWS regions hosting your website) - a primary resource and a secondary resource. When both resources are healthy and available, all the incoming traffic is directed to the primary resource. However, if the primary resource becomes unavailable due to any reason, Route 53's health checking agents continuously monitor the health of both resources. As soon as the primary resource goes down, Route 53 automatically directs all the traffic to the secondary resource, ensuring your application remains accessible even during failures.

**Example:**

Let's say you have your website hosted in two AWS regions: "Mumbai" and "Sydney." You designate "Mumbai" as the primary resource and "Sydney" as the secondary resource. When both regions are up and running, all users are directed to the "Mumbai" region. But if there's an issue in "Mumbai" (e.g., a server outage or network problem), Route 53 detects the unavailability and instantly switches all the traffic to the "Sydney" region, ensuring continuous access to your website.

### Steps to Create Failover Routing Policy in AWS Route 53 with an AWS Domain

For the Failover routing policy, we need to have a minimum of two load balancers. Similar to the steps we followed for creating load balancers in the Simple, Weighted, and Latency policies, we will first create a load balancer with a few EC2 instances in the Mumbai region. Next, we'll create another load balancer with a single EC2 instance in the Sydney region. After creating the load balancers, we need to set up a health check, where we will attach the Mumbai region's load balancer.

#### Setting Up Health Check

1. For the Failover policy, Health check is mandatory.
2. Click on "Health check."
3. Click on "Create health check."
4. Enter the name for the health check.
5. Select "Specify endpoint by domain name."
6. Set the protocol as "HTTP."
7. In the domain name field, enter the DNS name of the Mumbai load balancer.
8. Set the port number to 80.
9. For the path, enter "/index.html."
10. Click on "Advanced configuration."
11. Set the request interval as "Fast (10 Seconds)."
12. Set the failure threshold as "1."
13. Click on "Next."
14. Click on "Create Health check."

#### Adding Failover Routing Policy

1. Click on "Hosted Zones."
2. Click on "Create record."
3. Enter the route name.
4. Click on "Alias."
5. Select the application load balancer.
6. Choose the Mumbai region.
7. Select the load balancer.
8. Set the route policy to "Failover."
9. Choose the Failover record type as "Primary."
10. Select the health check that we created earlier.
11. Enter the Record ID.
12. Click on "Add another record."
13. Similarly, create the record for the Sydney region.
14. Choose the Failover record type as "Secondary."
15. Enter the Record ID.
16. Click on "Evaluate target health."
17. Click on "Create record."

Now, the Failover routing policy is set up for your domain. To check if it's working correctly, stop both the Mumbai instances and wait for a few minutes. Then, check the domain to see if the Failover policy is routing traffic to the secondary region (Sydney).

With the Failover Routing Policy, you can create a resilient and highly available architecture for your application. Route 53's health checks ensure that users are seamlessly redirected to the backup resource when the primary resource faces issues, providing a smooth and reliable user experience.


## Geolocation Routing Policy

The Geolocation Routing Policy in AWS Route 53 allows you to direct traffic based on the geographic location of your users. With this policy, you can choose where your traffic will be sent based on the continent, country, or state (only applicable in the US) from which the users are accessing your application or website.

**How It Works:**

With Geolocation Routing, you can define specific rules to route traffic based on the physical location of your users. For example, you can create different record sets in Route 53 and specify that users from Europe are directed to one resource, users from Asia to another resource, and users from the US to a third resource. This enables you to optimize the user experience and provide localized content to your users based on their location.

**Example:**

Suppose you have an e-commerce website, and you want to provide the best experience for users based on their location. You can set up Geolocation Routing in Route 53 as follows:

- Users from Europe are directed to servers located in the EU data center to ensure lower latency and faster response times.

- Users from Asia are routed to servers in the APAC data center to improve the website's performance for them.

- Users from the US are directed to servers in the US data center, ensuring a localized shopping experience.

### Steps to Create Geolocation Routing Policy in AWS Route 53

For the Geolocation routing policy, similar to the steps we followed for creating load balancers in other policies, we need to have two load balancers—one in the Mumbai region and another in the Sydney region. Once the load balancers are set up, we will create records in Route 53 for the Geolocation policy. The Geolocation policy allows you to route traffic based on the geographic location of your users. You can specify locations by continent, country, or state (only in the US).

**Here are the steps to create the Geolocation routing policy in AWS Route 53:**

Step 1: Click on "Create Record" in the AWS Route 53 dashboard.

Step 2: Enter a unique route name for the record. For example, you can use "www" to create a subdomain like "www.example.com."

Step 3: Click on "Alias" to associate the record with a resource. Select the application load balancer you previously created in the Mumbai region.

Step 4: Choose the appropriate load balancer from the list. In this case, you will select the load balancer in the Mumbai region.

Step 5: For the routing policy, choose "Geolocation." This will enable the Geolocation routing policy for this record.

Step 6: Click on "Evaluate target health" to enable health checking for the record. This ensures that traffic is only routed to healthy resources.

Step 7: Select the location as "India." Here, you specify the geographic location for which you want the traffic to be directed to the Mumbai region. You can also specify other locations such as continents, countries, or states (only applicable to the US) depending on your requirements.

Step 8: Enter a unique Record ID for this record. This ID helps in identifying the record and managing it within the Route 53 hosted zone.

Step 9: Click on "Add Another Record" to create another record for the Sydney region.

Step 10: For this new record, select the location as "United States." This will route traffic from the US to the Sydney region.

Step 11: Enter a unique Record ID for this record as well.

Step 12: Click on "Create Records" to create the Geolocation routing policy for your domain.

### Geolocation Policy (Default)

The Geolocation Policy (Default) is used when there is no specific geographic match for a user's location. In other words, if a user's location doesn't match any of the defined locations in the Geolocation routing policy, the default location will be used.  

For example, let's say you have two regions for your website: Mumbai and Sydney. You want to route traffic from users located in India to the Mumbai region, while all other users from around the world should be redirected to the Sydney region. In this scenario, you would configure the Geolocation routing policy with a specific location for India, and then set the Default location to redirect all other users to the Sydney region.

**Here are the steps to create the Geolocation Policy (Default) for your domain:**

Step 1: Enter the record Name. This can be the same as the previous record or a different subdomain, depending on your setup.

Step 2: Enter the route name. This can be the same as the previous record or a different name for organizational purposes.

Step 3: Click on "Alias" and select the application load balancer in the Sydney region.

Step 4: Choose the load balancer from the list.

Step 5: For the routing policy, choose "Geolocation" to enable the Geolocation routing policy for this record.

Step 6: Click on "Evaluate target health" to enable health checking for the record.

Step 7: Select the location as "Default." This location is used when a user's location doesn't match any specific location defined in the Geolocation routing policy. Traffic from such users will be directed to the resources in the Sydney region by default.

Step 8: Enter a unique Record ID for this record.

Step 9: Click on "Create record" to create the Geolocation Policy (Default) for your domain.

By configuring the Geolocation routing policy with specific locations and a default location, you can direct traffic to the most appropriate resources based on the geographic location of your users, providing them with a better user experience and optimized content delivery.



## Multivalue Routing Policy

Multivalue routing is a powerful feature in AWS Route 53 that allows returning multiple values, such as IP addresses for web servers, in response to DNS queries. This approach also helps in checking the health of each resource, ensuring that only values for healthy resources are returned. Although it is not a substitute for a load balancer, multivalue routing can significantly improve availability and load balancing by using DNS effectively.

Route 53 can respond to DNS queries with up to eight healthy records and provides different answers to different DNS resolvers. If you don't associate a health check with a multivalue answer record, Route 53 considers the record to be healthy by default. When you have eight or fewer healthy records, Route 53 responds to all DNS queries with all the healthy records. However, when all records are unhealthy, Route 53 responds to DNS queries with up to eight unhealthy records

**How It Works:**

With Multivalue Routing, you can create multiple record sets in Route 53 and associate each record set with a different IP address or resource. When a DNS query is received, Route 53 responds with multiple values for the specified domain name. This way, your application's traffic is distributed across multiple resources, allowing you to handle more requests and providing fault tolerance in case one of the resources becomes unavailable.

**Example:**

Let's say you have a high-traffic website that needs to be highly available. You can use the Multivalue Routing Policy in Route 53 as follows:

- Create three record sets in Route 53, each associated with a different IP address of web servers hosting your website.

- When users make DNS queries to access your website, Route 53 will respond with all three IP addresses.

- Users' web browsers will then choose one of the IP addresses to connect to, distributing the traffic among the web servers.

### Steps to Create Multivalue Routing Policy in AWS Route 53

**Step 1: Create Health Checks for both regions:**

1. Click on "Create Health Check" in the AWS Route 53 dashboard.
2. Enter a name for the health check, e.g., "Mumbai Health Check."
3. Enter the IP Address of the machine in the Mumbai region (First Machine) that you want to monitor.
4. Click on "Next."
5. Configure additional settings as needed for the health check.
6. Click on "Create Health Check" to save the settings.
7. Repeat the above steps to create a health check for another region, e.g., "Sydney Health Check."

**Step 2: Create Multivalue Records for mumbai region in Route 53:**

1. Click on "Hosted Zones" in the AWS Route 53 dashboard.
2. Select your domain name from the list.
3. Click on "Create Record" to add a new record set for your domain.
4. Enter the record name as "www" or any subdomain you prefer.
5. Enter the public IP address of the machine in the Mumbai region in the "Value" field.
6. Set the TTL (Time-to-Live) as 1 minute (1M).
7. For the routing policy, choose "Multivalue Answer."
8. Select the health check you created earlier for the Mumbai region.
9. Enter a unique Record ID for this record.
10. Click on "Create Records" to create the multivalue answer record for the Mumbai region.

**Step 3: Add Multivalue Answer Record for Sydney Region:**

1. Click on "Create Record" to add another record set for your domain.
2. Enter the record name as "www" or any subdomain you prefer.
3. Enter the public IP address of the machine in the Sydney region in the "Value" field.
4. Set the TTL (Time-to-Live) as 1 minute (1M).
5. For the routing policy, choose "Multivalue Answer."
6. Select the health check you created earlier for the Sydney region.
7. Enter a unique Record ID for this record.
8. Click on "Create Records" to create the multivalue answer record for the Sydney region.

**Step 4: Verify the Multivalue Routing Policy:**

1. Now, you can check the domain name in multiple systems to observe how the multivalue routing policy returns different IP addresses based on health checks and DNS resolvers.

By following these steps, you have successfully configured a Multivalue Routing Policy in AWS Route 53, enhancing the availability and load balancing capabilities of your website across different regions.


## Setting up AWS EC2 with 3rd Party Domain using Simple Routing Policy

### Introduction
This guide provides step-by-step instructions to set up an AWS EC2 instance and configure it with a third-party domain using the Simple Routing Policy in AWS Route 53.

### Prerequisites
1. An AWS account with appropriate permissions to create EC2 instances and manage Route 53.
2. A domain purchased from a domain registrar like GoDaddy or Hostinger.

### Steps
1. **Buy Domain**: Purchase the desired domain (e.g., example.com) from a domain registrar like GoDaddy or Hostinger.

2. **Create EC2 Machine**: Set up an EC2 instance on AWS to host your website or application.

3. **Add Bootstrap Script**: Use the provided bootstrap script to automate the configuration process on the EC2 instance.

4. **Create Security Group**: Create a security group for the EC2 instance to control inbound and outbound traffic.

5. **Enable SSH Port & HTTP**: Configure the security group to allow SSH access (port 22) and HTTP access (port 80) to the EC2 instance.

6. **Copy the Public IP**: Take note of the public IP address of the EC2 instance, which will be used for routing traffic.

7. **Go to Route 53**: Navigate to the AWS Route 53 service to manage DNS settings.

8. **Go to Hosted Zone**: Access the Hosted Zone section in Route 53 to manage domain names and DNS records.

9. **Click on Create Hosted Zone**: Create a new hosted zone for your domain (e.g., example.com).

10. **Enter Domain Name**: Enter your domain name (e.g., example.com) and add an optional description.

11. **Select Type as Public Hosted Zone**: Specify that this hosted zone is publicly accessible for internet traffic.

12. **Click on Create Hosted Zone**: Create the hosted zone to proceed with DNS configuration.

13. **Click on Create Record**: Within the hosted zone, create DNS records to route traffic.

14. **Select Record Type as Route Traffic to an IPV4**: Choose the "A" record type to route traffic to an IPv4 address.

15. **Enter Value as Public IP Address of Our EC2 Machine**: Enter the public IP address of your EC2 instance.

16. **Select TTL (Time to Live) as 60**: Set the Time to Live (TTL) to 60 seconds to control DNS caching.

17. **Click on Create Records**: Create the "A" record to link your domain (example.com) to the EC2 instance's public IP address.

18. **Create One More Record**: Additionally, create another DNS record.

19. **Enter Record Name**: Set a name for the record, e.g., "www".

20. **Select Record Type as CNAME Routes Traffic to Another Domain**: Choose the "CNAME" record type to create a subdomain that points to another domain.

21. **In the Value Enter as Domain Name**: Enter the domain name (e.g., "subdomain.example.com") that the subdomain should point to.

22. **Click on Create Records**: Create the "CNAME" record to route traffic from the subdomain (e.g., "www.example.com") to the specified domain (e.g., "subdomain.example.com").

23. **Note Down the Values for Type NS**: Take note of the NS (Name Server) values provided by Route 53.

24. **Go to the Domain Provider Website**: Visit the website of the third-party domain provider (GoDaddy, Hostinger, etc.) where you purchased the domain (example.com).

25. **Click on Change Nameservers**: Access the DNS settings for your domain.

26. **Select Change Nameservers**: Choose to change the nameservers associated with the domain.

27. **Enter the DNS Names**: Enter the NS (Name Server) values obtained from Route 53 to allow Route 53 to handle DNS requests for the domain.

28. **Click on Save**: Save the changes to update the nameservers for the domain.

29. **Now Check the Website**: After DNS propagation, the domain (example.com) will be successfully configured with AWS EC2 instances using a Simple Routing Policy. You can access the website using the domain name and verify its functionality.




