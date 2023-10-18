### Creating an IAM role for authorizing EC2 instance to send logs to Cloudwatch logs:
- Create a role and then assign an Inline Policy to the role with the following permisions:
  * DescribeLogStreams
  * CreateLogGroup
  * CreateLogStream
  * PutLogEvents

- We can also edit the permissions while creating the role itself and write this [code](https://github.com/warlock601/AWS/blob/f1f1007c71278027256bf98443dcbac9b08a5c68/Logging%2C%20Monitoring%20and%20Storage%20solution%20for%20EC2%20instances/IAM%20role/code.txt)
