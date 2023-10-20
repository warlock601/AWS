### Configuring stress utility on EC2 instance

First become a super user.

```bash
  sudo su
```

Installing epel package.
```bash
  amazon-linux extras install epel
```

Installing stress utility.
```bash
  yum install stress -y
```

Running stress to increase CPU load.
```bash
  stress --cpu 8 --timeout 300    
```


This above command will run the stress utility for a total of 300s <br />
<br />
<br />
After running this, we'll see that CPU utilization will suddenly peak in the dashboards and we'll receive email from the SNS topic that we subscribed to.
