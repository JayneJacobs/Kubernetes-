# DNS

built in DNS

launched and configured automatically. 

Every service gets a DNS name

# nomenclature
www - hostname
google - domainname
.com - top-level domain name
.com - top-level domain name

servicename.namespace.svc.cluster.local

predictable defaults. 

Namespaces:
   Separate Kluster into narower clusters
   For large Klusters. 

1. Set up [deployment yml. ](WordPress/deployment.yml)
2. kubectl create -f my-sql-deployment.yaml
3. kubectl create -f wordpress-deployment.yaml

```sh
$ kubectl get services wordpress
NAME        TYPE           CLUSTER-IP     EXTERNAL-IP   PORT(S)        AGE
wordpress   LoadBalancer   10.99.65.153   <pending>     80:30634/TCP   8m46s
$ minikube service wordpress  --url
http://192.168.99.100:30634
```

kubectl get persistentvolumes
