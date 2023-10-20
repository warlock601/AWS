### 1. CloudWatch > Dashboard > Create Dashboard. Give a name to your dashboard.

### 2. We'll create different widgets for CPU utilization, Network packets in/out, Status check.
- For CPU utilization widget, select CPU utilization. Metrics > EC2 > Pre-instance metrics > select CPUUtilization

### 3. Similarly create dashboards for Network in/out and Status check as well.

### 4. Create an Alarm, Select metric > EC2 > Pre-instance metrics > CPU Utilization. Then, we can specify a condition as Greater than 90.
- Configure Actions > Alarm state trigger, in-alarm > Create a new topic > enter a topic name and email.

Now to check, we'll install [Stress utility](https://github.com/warlock601/AWS/blob/a3ff470f1813bf5f883f5b564f9df87f0ba72b65/Cloudwatch%20Dashboard%2C%20Alarm%20using%20SNS/stress%20utility.md) in our EC2 instance.
