### 1. First we'll create a VPC as they want a monitoring and reporting layer so we'll use a VPC so that we can then monitor our whole architecture.
Create a VPC and specify IPv4 CIDR block- 10.0.0.0/24
- Create a subnet inside that VPC by selecting that VPC id.

- IPv4 VPC CIDR block will be selected by defualt.

- Choose IPv4 subnet CIDR block as 10.0.0.0/26 or depending upon the no. of IPs you want.

### 2. Then we'll create an Internet Gateway, attach that IGW to the VPC we created. 

### 3. Then we'll create a route for this IGW in the route table of our VPC.
- Open Rotte table > Edit Routes, then add Destination = 0.0.0.0/0 and select that Internet Gateway as Target.
### 4. Create a Security Group and select this VPC and the subnet we created.
- It should allow SSH from anywhere(0.0.0.0/0) on port-22.

### 5. Create an EC2 instance by associating the security group we created (select the VPC in nwhich that SG was created and then only we can associate that SG).
NOTE: We'll attach an Elastic IP to this instance otherwise we won't to able to connect to this instance through EC2 connect as it does now have any public IPv4 address.

![Screenshot 2023-10-20 141319](https://github.com/warlock601/AWS/assets/32487715/d5b82bd8-08c0-446f-a441-aafac1b5a240)


Let's proceed to [CloudWatch section](https://github.com/warlock601/AWS/blob/d65436fef57f95574db117b7f0f5cc773fdf9698/Cloudwatch%20Dashboard%2C%20Alarm%20using%20SNS/CloudWatch/README.md)
