# Logging, Monitoring and Storage solution for EC2 instances


I implemented a logging of EC2 logs in Cloudwatch log Group. Detailed monitoring for EC2 is enabled so that log data is available at 1-minute period. 
After the EC2 logs are sent to CloudWatch log group, these logs are stored in S3 bucket so that these logs are backed up for safety and available for reference in case of any security incidents. I created IAM roles for EC2 instances, installed CloudWatch log agent and created S3 bucket policies.

You can start from [here](https://github.com/warlock601/AWS/blob/bcbdcce36c486fd7942fc40eab4cd56c4f3d743c/Logging%2C%20Monitoring%20and%20Storage%20solution%20for%20EC2%20instances/EC2%20instance/README.md)
## Screenshots

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)
