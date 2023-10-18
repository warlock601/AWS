### 1. Installing EC2 instance-
- Use Amazon linux 2 AMI instaed of AMI 2023 to launch the instance.
- Create a key-pair so that we can SSH into the instance later if we want to.
- Connect to the instance using either terminal or EC2 instance connect.

Note: Before Installing thus, create an IAM role with appropriate permissions (check it out [here](https://github.com/warlock601/AWS/tree/f1f1007c71278027256bf98443dcbac9b08a5c68/Logging%2C%20Monitoring%20and%20Storage%20solution%20for%20EC2%20instances/IAM%20role) )
### Also enable the detailed monitoring for EC2 instance.
![Screenshot 2023-10-19 001904](https://github.com/warlock601/AWS/assets/32487715/64fb26c1-f675-4eba-981e-823707dec664)

### 2. Installing AWS Cloudwatch logs agent on the instance-
- First we'll update the packages.

```bash
  sudo yum install -y
```

- Install the awslogs package

```bash
  sudo yum install -y awslogs
```
### 3. Then Edit the configuration file in /etc/awslogs/awslogs.conf with the given [configuration](https://github.com/warlock601/AWS/blob/f124012071a0ca6b14204019d9b28ca613366404/Logging%2C%20Monitoring%20and%20Storage%20solution%20for%20EC2%20instances/EC2%20instance/configuration.txt)
### 4. Then start the AWS logs service and enable the service to start at each system boot.
```bash
  sudo systemctl start awslogsd
  sudo systemctl enable awslogsd.service
  sudo systemctl status awslogsd
```
