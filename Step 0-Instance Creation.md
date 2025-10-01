
---

In AWS account create an instance in **eu-west-3** (Paris) 
(You need an instance since the cloud shell has not enough space to run the deployment(1gb))

==-Note:== you can use other region but you will need to [[Change AMIS in Terraform]]

Go To -> EC2 -> Instances -> Launch Instance

Instance specification as follows:

- Name: (whatever you want)

- AMI: Amazon Linux 2023 kernel-6.12

- Instance type: t2.medium
(other types are ok too you don't need much CPU for this instance)

- In **Key pair** we need to create a key otherwise we will not be able to ssh connect to the instance

Click on create new **Key pair**:

-pick a name
-select RSA type
-select .pem file format

And create the **Key pair** 
(remember to store it in a safe please and do not lose it otherwise you will not be able to login into the instance using key pairs)


- In **Network Settings** select **Create security group**, mark the following:

-Allow SSH traffic from 
-Allow HTTPS traffic from the internet
-Allow HTTP traffic from the internet

And ip range: Anywhere 0.0.0.0/0

==-Note:== This configuration is very insecure but we just focus on using this instance for the deployment so when its done we can shutdown the instance; you can change the VPC's configuration later.

- Configuration Storage: 1x 20gb / gp3


 Leave everything else as default and click **Launch instance** 