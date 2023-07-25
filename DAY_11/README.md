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

**Steps to Create Simple Routing Policy in AWS Route 53:**

To use the Simple Routing Policy in Route 53, follow these steps:

1. Sign in to the AWS Management Console and navigate to the Route 53 dashboard.
2. Select the hosted zone for your domain.
3. Create a new record set (e.g., "www.example.com").
4. Choose the Simple routing policy option.
5. Enter the relevant resource record values, such as the IP address for your website.
6. Save the changes.

**Important Considerations**

- The Simple Routing Policy is best suited for scenarios where you have a single resource, such as a website, hosted in a specific region to handle a particular function for your domain.
- If you have multiple resources in different regions and want to route traffic based on latency, geographic location, or other criteria, consider using other routing policies available in Route 53.

In summary, the Simple Routing Policy is an easy and straightforward way to route traffic to a single resource in a specific region for your domain in AWS Route 53.


## Weighted Routing Policy

The Weighted Routing Policy in AWS Route 53 allows you to divide website traffic between different resources or regions based on specific percentages that you assign. It's like splitting incoming visitors to your website into different groups, and each group is sent to a different location based on the weight you set.

**How It Works:**

Imagine you have two regions, "AP South 1" and "AP East 1," and you want to distribute traffic between them. With the Weighted Routing Policy, you can configure the percentages for each region. For example:

- 80% of website visitors go to servers in "AP South 1."
- 20% of website visitors go to servers in "AP East 1."

**Example:**

Let's say you have an online store, and during a special promotion, you expect a high volume of traffic. You want to ensure both "AP South 1" and "AP East 1" regions handle the load efficiently. By using the Weighted Routing Policy, you can direct more visitors to "AP South 1" to handle the majority of the traffic while still sending some traffic to "AP East 1."

This way, you can control the distribution of traffic and ensure both regions are utilized effectively to provide a smooth experience for your website visitors.

**Steps to Create Weighted Routing Policy in AWS Route 53:**

1. Sign in to the AWS Management Console and navigate to the Route 53 dashboard.

2. Click on "Create Record Set" for the domain you want to configure.

3. Select "Weighted" from the Routing Policy drop-down menu.

4. Enter the desired values for "Name" and "Type." For example, "www" and "A."

5. In the "Value" field, add the IP address or resource record of the server or resource in "AP South 1."

6. Set the "Weight" to 80 to indicate that 80% of traffic should go to "AP South 1."

7. Click on "Define Weighted Record" to add another record set for "AP East 1."

8. In the "Value" field, add the IP address or resource record of the server or resource in "AP East 1."

9. Set the "Weight" to 20 to indicate that 20% of traffic should go to "AP East 1."

10. Review the settings and click "Create" to apply the Weighted Routing Policy.

With the Weighted Routing Policy set up, Route 53 will automatically distribute incoming traffic between the specified regions based on the assigned weights. This allows you to balance traffic load and ensure high availability and performance across your resources.


## Latency-Based Routing Policy

The Latency-Based Routing Policy in AWS Route 53 helps ensure that your website visitors are directed to the AWS region that provides the lowest network latency or fastest response time. It's like guiding your users to the server location that can deliver the website content with the least delay.

**How It Works:**

When a user tries to access your website, AWS Route 53 measures the network latency or the time it takes for data to travel between the user's location and the different AWS regions where your website is hosted. It then directs the user to the AWS region with the lowest latency, which should offer the quickest response time.

**Example:**

Let's say you have your website hosted in two AWS regions: "US East" and "US West." When a user from India visits your website, Route 53 will measure the latency to both regions. If the user is physically closer to "US West," Route 53 will direct them to the servers in that region because it provides the fastest response time for the user in India.

**Steps to Implement Latency-Based Routing Policy in AWS Route 53:**

1. Sign in to the AWS Management Console and navigate to the Route 53 dashboard.

2. Click on "Create Record Set" for the domain you want to configure.

3. Select "Latency" from the Routing Policy drop-down menu.

4. Enter the desired values for "Name" and "Type." For example, "www" and "A."

5. In the "Value" field, add the IP address or resource record of the server in the "US East" region.

6. Click on "Define Latency Record" to add another record set for the "US West" region.

7. In the "Value" field, add the IP address or resource record of the server in the "US West" region.

8. Review the settings and click "Create" to apply the Latency-Based Routing Policy.

With the Latency-Based Routing Policy, Route 53 will automatically direct users to the AWS region that offers the lowest network latency for their location. This ensures that your website's content is delivered with minimal delay, providing a smoother and faster user experience.


