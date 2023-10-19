We create an S3 bucket to store the logs.

After creating the bucket, we will edit the bucket policy to allow AWS logs to be stored in the bucket.

go to Permissions > Bucket Policy > Edit. Then create the policy from policy generator that'll allow aws logs to access the bcuket for them
to be stored. Or else you can copy the bucket policy from [here](https://github.com/warlock601/AWS/blob/59875821f11f1a684290faa771870184242fb0f1/Logging%2C%20Monitoring%20and%20Storage%20solution%20for%20EC2%20instances/S3/policy.txt).
