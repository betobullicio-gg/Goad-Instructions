
---


For the final step you will need to run the provisioning and from this you need to connect to your ec2 instance used for the deployment (you can also directly ssh connect to your jumpbox and jump to the command `load <instance_id>`).

In your instance go to your GOAD folder and run:

```
python3 goad.sh
```

this will launch the GOAD console where you can made different configurations, from here use it to connect to your jumpbox with the command:

```
ssh_jumpbox
```

When you are there just run the following commands in order:

```
create_empty 
load <instance_id>
provide
sync_source_jumpbox
prepare_jumpbox
```

==Note:== you can skip the `create_empty` command if you want and use the already created instance during the deployment, you can get its id at the start of the GOAD console.

If you don't get any error and everything checks ok run the following command and start the provisioning:

```
provision_lab
```

It will take approximately 20-25 minutes

You will need to press Ctrl+c and then c enter (just like on the deployment) so be sure to keep alive your session.

After it finish congratulations!!! You will finally have your lab complete. Yay :) 