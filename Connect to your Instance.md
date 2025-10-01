
---

There are multiple ways you can use to start the connection with your ec2 instance; you will need this since you will run multiple configurations on it.

First you need select your instance and click Connect

Here you can pick 2 options

**Simply Connect:**

If you have your key-pair of the instance in your current account and have the right privileges you can click connect on the first tab, you will use the public ip of the instance and automatically start and ssh session.

**SSH client:**

Or you can also run a command in your terminal to connect to it.

You will need to have your key in your session if you are using cloud shell, if you are in your computer you will need to have the file of the key and point to it, use the command to connect:

```
ssh -i "your-key.pem" ec2-user@ec2-1-1-1-1.eu-west-3.compute.amazonaws.com
```

And with that you can connect using any ssh client you want.




##### Connect to your Jumpbox Instance

Here you will need the key of the jumpbox instance created in the deployment phase, you get this in [[Ways to get the ssh-key]] .

With that you just need to specify the path where you storage your ssh key and run the following command:

```
ssh -t -o StrictHostKeyChecking=no -i /home/ec2-user/GOAD/workspace/<instance_id>/ssh_keys/ubuntu-jumpbox.pem goad@1.1.1.1
```
