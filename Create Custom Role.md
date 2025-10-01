
---

You can create a custom role if you find the default ones over permissive and you want to keep you environment more secure.

Go To -> IAM -> Roles -> Create role

-Choose AWS service
-EC2/EC2
-Skip attaching any policy
-Name the role
-Create role

Now in roles look for your created role
Then look for the permissions tab and in Add permissions select: Create inline policy
You can create it using the GUI but here we will use the JSON option
Change to JSON and copy the following:

```
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Sid": "VisualEditor0",
			"Effect": "Allow",
			"Action": "s3:PutObject",
			"Resource": "arn:aws:s3:*:889393247587:accesspoint/*/object/*"
		}
	]
}
```

Click Next
Pick a Name
And create the policy



Just like that you can create your custom roles!