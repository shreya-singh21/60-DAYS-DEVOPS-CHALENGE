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

### How It Works

Imagine you have a website hosted on an EC2 instance in the US-West (Oregon) region with the IP address "203.0.113.10". When a user enters your domain name (e.g., www.example.com) in their web browser, their computer sends a DNS query to AWS Route 53 to resolve the domain name to an IP address.

With the Simple Routing Policy, Route 53 looks at the resource record set associated with the domain (e.g., the "A" record), which contains the IP address "203.0.113.10" for your website. Route 53 then responds to the DNS query with this IP address. The user's web browser can now use this IP address to connect to your website hosted in the US-West (Oregon) region.

### Usage

To use the Simple Routing Policy in Route 53, follow these steps:

1. Sign in to the AWS Management Console and navigate to the Route 53 dashboard.
2. Select the hosted zone for your domain.
3. Create a new record set (e.g., "www.example.com").
4. Choose the Simple routing policy option.
5. Enter the relevant resource record values, such as the IP address for your website.
6. Save the changes.

### Important Considerations

- The Simple Routing Policy is best suited for scenarios where you have a single resource, such as a website, hosted in a specific region to handle a particular function for your domain.
- If you have multiple resources in different regions and want to route traffic based on latency, geographic location, or other criteria, consider using other routing policies available in Route 53.

In summary, the Simple Routing Policy is an easy and straightforward way to route traffic to a single resource in a specific region for your domain in AWS Route 53.
