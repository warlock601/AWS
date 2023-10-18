### Creating an IAM role for authorizing EC2 instance to send logs to Cloudwatch logs:
- Create a role and then assign an Inline Policy to the role with the following permisions:
  * DescribeLogStreams
  * CreateLogGroup
  * CreateLogStream
  * PutLogEvents

- We can also edit the permissions while creating the role itself and write this code.
