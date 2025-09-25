
---

You will need some python libraries and modules before start the installation process.
Run the following commands in order to get them.

==Note:== Personal recommendation run the installation of packets separately since if you try to download them all at once you can encounter some issues.

Commands:

```
sudo yum install git -y
```

```
sudo yum install python3-pip -y
```

```
pip3 install ansible boto3 psutil pywinrm requests proxmoxer rich ansible_runner
```

You can check if the packages were installed with:

For git and pip:

```
git --version
pip3 --version
```

For python modules:

```
python3 -c "import boto3; print(boto3.__version__)"
```

(just change to the module you want to check)


Next download terraform zip file

```
curl -LO https://releases.hashicorp.com/terraform/1.9.8/terraform_1.9.8_linux_amd64.zip

unzip terraform_1.9.8_linux_amd64.zip

sudo mv terraform /usr/local/bin/
sudo mv LICENSE.txt /usr/local/bin/  #move the file to bin folder
```

==Note:== you can remove the .zip terraform file leftover with:

```
rm terraform_1.9.8_linux_amd64.zip
```

And to check if the installation succeed:

```
terraform --version
```

- Final requirement is to clone the GOAD repository into our instance

```
git clone https://github.com/Orange-Cyberdefense/GOAD.git
```

And check if the directory copies correctly

```
cd GOAD
```


List of Requirements:

- [ ] git
- [ ] python3-pip
- [ ] ansible
- [ ] boto3
- [ ] psutil
- [ ] pywinrm
- [ ] requests
- [ ] rich
- [ ] ansible_runner
- [ ] python-terraform
- [ ] proxmoxer
- [ ] terraform.exe
- [ ] clone the GOAD repository