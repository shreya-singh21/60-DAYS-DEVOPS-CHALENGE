## Reachability Analyzer

VPC Reachability Analyzer is a configuration analysis tool that enables us to perform connectivity testing between a source resource and a destination resource in our virtual private clouds (VPCs). At times, when customers are deploying large workloads in AWS, it is also quite difficult and time consuming to troubleshoot network connectivity issues mainly due to misconfigurations. This is where VPC Reachability Analyzer can help.

1. Create VPC.

2. Give the VPC name.

3. Enter IPV4 CIDR
   ex- 10.0.0.0/16

4. Create VPC.

5. Create Subnet.

6. Click on subnets

7. Select your VPC 

8. Enter subnet name, Select availability zone & Enter 10.0.1.0/16 CIDR Block.

9. Click on Create subnet.

10. Click on edit Subnet setting.

11. click on enable auto assign public IPv4 address.

12. Go to internet gateway.

13. Give the name of internet gateway

14. create internet gateway

15. After creation of internet gateway will get popup saying that "Attach to a VPC". Click on that popup.

16. Create route table.

17. Click on route table

18. Give the name of route table

19. Select your VPC

20. Click on create route table.

21. Edit Subnet Association

22. Edit routes

23. Click on add routes

24. Select Internet Gateway as target

25. Give 0.0.0.0 as destination. 0.0.0.0 means open to all.

26. Create Linux EC2 Machine in our VPC & Subnet

27. Enable SSH Port 

28. Go to VPC

29. Click on Reachability Analyzer 

30. Click on create and analyze path

31. Enter the name

32. Select sourec and destination means from which source and destination you want to check connectivity.

33. Select the Source type (Instances)

34. Select the source as EC2

35. Select the Destination type (Internet Gateway)

36. Select the destination as Internet gateway ID

37. Click on create and analyze path

38. Now in Reachability Analyzer you will see the whole path

39. Now if you disconnect the connectivity means if you remove the internet gateway from route table 

40. Check the Reachability Analyzer. Go to Action and view details you will find one more time it will run and it shows error. You can check where error is showing and you can rectify it.




