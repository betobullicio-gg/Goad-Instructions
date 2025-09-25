
---

Finally you just need to run the installation script under the GOAD directory

```
cd GOAD

python3 goad.py -p aws -t install -d azure
```

==Note:== we use the -d flag to exclude the use of the module for azure since we do not require it; this is a way to avoid download unnecessary packages and exclude them from being executed on the code so we avoid that possible error too.