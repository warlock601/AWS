1. We create an S3 bucket to store the logs.  Note: Create the bucket in the same region as CloudWatch log groups region ie, N.Virginia.

2. After creating the bucket, we will edit the bucket policy to allow AWS logs to be stored in the bucket.

3. Go to Permissions > Bucket Policy > Edit. Then create the policy from policy generator that'll allow aws logs to access the bcuket for them
to be stored. Or else you can copy the bucket policy from [here](https://github.com/warlock601/AWS/blob/59875821f11f1a684290faa771870184242fb0f1/Logging%2C%20Monitoring%20and%20Storage%20solution%20for%20EC2%20instances/S3/policy.txt).
Add your own Account ID and also mention your own bucket name in the policy and save it.

4. Then we're gonna export the logs onto the S3 bucket. Open CloudWatch and click on the log group and then Actions > Export data to Amazon S3.

![Screenshot 2023-10-19 145748](https://github.com/warlock601/AWS/assets/32487715/491d910b-7893-453e-a77d-0842dc7df2f1)

