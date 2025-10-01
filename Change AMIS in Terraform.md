
---

If you want to use other region you will need to change the AMIS in each .tf file

- First look for available AMI for your AWS region with command

```
aws ec2 describe-images \
    --owners amazon \
    --filters "Name=name,Values=Windows_Server-2019-English-Full-Base-*" \
              "Name=platform,Values=windows" \
              "Name=architecture,Values=x86_64" \
              "Name=virtualization-type,Values=hvm" \
              "Name=root-device-type,Values=ebs" \
    --region us-east-1 \
    --query "Images[*].[ImageId,Name,CreationDate]" \
    --output table
```

Change the region an used name for any specifications like Windows server or a jump box, output looks like this:

ami-043cf96255cd85b98   Windows_Server-2019-English-Full-Base-2025.08.13        
ami-0623bc4c9a53fe562    Windows_Server-2019-English-Full-Base-2025.07.09         
ami-0f6d3d1de3c02ee19   Windows_Server-2019-English-Full-Base-2025.09.10                      


- Next locate all the .tf files in the GOAD directory so you can edit them, all recognizable locations are:

-ad/GOAD/providers/aws/windows.tf
-extensions/exchange/providers/aws/windows.tf
-extensions/ws01/providers/aws/windows.tf
-template/provider/aws/jumpbox.tf

Move to the directory with the command cd /path/here/

- Next you should use nano to edit the files in each directory and replace the  value for a valid one for your region

```
nano windows.tf
```

you will get prompt this:

```
"srv01" = {
  name               = "srv01"
  domain             = "sevenkingdoms.local"
  windows_sku        = "2019-Datacenter"
  ami                = "ami-03440f0d88fea1060" #cahnge this value with your ami#
  instance_type      = "t2.xlarge"   # t2.xlarge = 4cpu / 16GB
  private_ip_address = "{{ip_range}}.21"
  password           = "FP.xh5Fk9Z1c"
}
```

Change the value inside `ami` with your valid AMI for your region.

Then ctrl+o and hit enter to save and ctrl+x to exit the file.
Do this with the different .tf files so you can get a valid AMI for each of them and you will be all set up!