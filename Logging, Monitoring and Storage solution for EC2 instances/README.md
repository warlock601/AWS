# Logging, Monitoring and Storage solution for EC2 instances


I implemented a logging of EC2 logs in Cloudwatch log Group. Detailed monitoring for EC2 is enabled so that log data is available at 1-minute period. 
After the EC2 logs are sent to CloudWatch log group, these logs are stored in S3 bucket so that these logs are backed up for safety and available for reference in case of any security incidents. I created IAM roles for EC2 instances, installed CloudWatch log agent and created S3 bucket policies.


## Screenshots

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)
