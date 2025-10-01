
---

Finally you just need to run the installation script under the GOAD directory, this will deploy all the infrastructure needed for the lab.

```
cd GOAD

python3 goad.py -p aws -t install -d azure
```

==Note:== we use the -d flag to exclude the use of the module for azure since we do not require them; this is a way to avoid download unnecessary packages and exclude them from being executed on the code so we avoid that possible error too.

Expect the deployment  process to take around 1:30 - 2:00 hours.

You need to press ==ctrl+c and then c== in one point of the deployment around 10-15 minutes after it started so make sure you do not lose connection to your session otherwise you will need to restart the deployment process and delete all the already ongoing infrastructure.