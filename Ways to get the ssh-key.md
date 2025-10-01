
---

One way to connect to the environment to apply the provisioning or directly interreact with it is using the jumpbox, for this you will need to establish a ssh session from your ssh client and for this you will need the key pair created during the deployment so you can initialize the session for the goad user.

#### **Option A: Directly Copy Paste the Key**

You can open the config files in the ec2 instance use for the deployment and in the path below you will find the .pem file for the ssh session:

`goad/workspaces/<instance_folder>/ssh_keys`

under this patch you can:

```
cat ubuntu-jumpbox.pem
```

This will open the file; copy its exact contents without making any changes, and paste them into a new text file. Save that file with a `.pem` extension — that will recreate the private key.



##### **Option B: Safe It Inside a s3 Bucket** 

For this option you need to create a s3 Bucket if you don't have one 

Creation of s3 Bucket:

Go To -> Amazon S3 -> Buckets -> Create bucket

-Pick a name for the bucket
-Leave everything else as default
-Create bucket


///////////

==*Optional*== 

You can create an IAM role an attached it to the instance so you can upload object to the bucket since you need `s3:PutObject` permission.

Although since for the deployment you attached the goad user to the `--profile` config of the instance and the goad user has admin access you don't need to attached this role in this way, but just as a reminder this is a more secure way to do it.

you can verify your `--profile` with:

```
aws sts get-caller-identity
```


Go To -> IAM -> Roles -> Create Role

-Select AWS service
-Use case EC2 / EC2
-Permission Policy: AmazonS3FullAccess 
(What you actually need is the `s3:PutObject` so you can define your own role to just allow upload of files) explain in [[Create Custom Role]]
-Pick a name
-Create role

And then just need to attach this role to the ec2 instance 

In instances pick your ec2 instance -> Actions -> Security -> Modify IAM role

-There just pick the role you created and Update IAM role

///////////

Now you just need to connect to your ec2 instance and download the file into your s3 bucket

```
aws s3 cp /path/to/your-key.pem s3://your-bucket-name/ssh-keys/your-key.pem
```

You will have your file downloaded to your bucket

Now there are 3 ways to downloaded it from your bucket to your computer:

- First: (Easiest)

Use your AWS console to navigate to your s3 bucket, find your file and simply click download, and just like that you will have it.

- Second: (Easy too)

Using your Cloud Shell in your session create a Temporal URL

```
aws s3 presign s3://your-bucket-name/ssh-keys/-your-key.pem --expires-in 30
```

the `--expires-in` flag is for the seconds, sine you just need to download 1 file you don't need to have it for a long period open.

Open the url and it will automatically will download the file.

- Third: (More config)

Also if you have your computer set up with the AWS Cloud Shell configurated with your session you can also run the following command:

```
aws s3 cp s3://your-bucket-name/ssh-keys/your-key.pem C:/Users/YourUser/Downloads/your-key.pem
```

And it will download the file to your computer.



##### **Option C: Create a Temporary Web Server with Python**

With this you can create a Web Server so you can access via your browser and download any need file.

Go to the directory where the key is:

```
cd GOAD/workspaces/<instance_folder>/ssh_keys/
```

Then run the following command:

```
python3 -m http.server 8000
```

And next on yourr browser go to:

`http://<EC2-IP>:8000/`

From there just make sure the file is there and proceed to download it.

You can also run this from a Linux terminal:

`wget http://<EC2-IP>:8000/path/to/file.txt`



##### **Option D: Using your ssh client Grab the file with `scp`**

You can use your cmd terminal and use the following command to grab the the file directly to your computer.

Notice that you will need to specify/be on the directory that has the key to ssh to your current instance where the file is on, also the instance needs to be running.

```
$ scp  -i C:/Users/Your/Path/to/key.pem  ec2-user@ec2-1-1-1-1.eu-west-3.compute.amazonaws.com:/home/ec2-user/GOAD/workspace/your_instance_folder/ssh_keys/ubuntu-jumpbox.pem C:/Users/Your/Desire/Path
ubuntu-jumpbox.pem 
```


And that way you will have a copy of the key directly into your computer.

==Note:== If you are using Windows you may want to have either a vm to run Linux commands or use the Git Bash cmd to run bash/Linux commands




