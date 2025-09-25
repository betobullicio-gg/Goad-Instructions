
---

You will also need a user who will be in charge of the configuration process since the script will use its credentials to manage the resources needed for the deployment.

Go To -> IAM -> Users -> Create user

Pick a name: `your-user`

Use Attach policies directly
select: AdministratorAccess

(bad practice but we will do it for efficiency sine this account is just for the deployment we can delete it later)

And hit **Create user**

Then in Users click for `your-user` and go to -> Security credentials tab -> look for Access key -> and click Create access key

Choose: Application running on an AWS compute service and click the **Confirmation** box, hit **Next**

And click **Create access key**

This would automatically downloads your user keys, safe them in a secure place and do not lose them since you would need them for later step. ([[Step 3-Create config Files]])