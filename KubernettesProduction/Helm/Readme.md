# Helm


* A Simple way to package and configure.  in on deployment. 

* Do not repeat coding principles 

* Configure a package and manage dependencies. 

* Update and remove containers. 

* Define run, upgrade for public distribution. 


## Helm Charts:

 * Kubernettes Yamls. 

 * helm/tiller runs on Kubernetes clusters. 

 * Helm sends charts to Tiller Server.  and tiller installs the package. 
   Basic
    ```
    helm install stable\chartName
    ```

* Tiller compiles yamls and applies them to cluster. 

Single CLI command line. 

Helm tool; 
  *Package description (yaml)
    Templates: Yaml files

 Accessing Helm Charts.
  repository
  Helm install; location of charts; chart name. 

  Charts define, run , upgrade. 

  official and unoffficial charts. 

#Install helm. 

https://github.com/helm/helm/releases


 tar -zxvf helm-v2.13.1-darwin-amd64.tar.gz 
 
  mv darwin-amd64/helm usr/local/bin/helm
   cd darwin-amd64/
 
 mv helm /usr/local/bin/

## Setup Tiller

```sh

kubectl get pods --all-namespaces=true
NAMESPACE     NAME    READY   STATUS    RESTARTS                   AGE
kube-system   event-exporter-v0.2.3-f9c896d75-kncs9  2/2     Running   0          14m


kubectl delete clusterrolebinding tiller
kubectl --namespace=kube-system create serviceaccount tiller
serviceaccount/tiller created

kubectl create clusterrolebinding tiller --clusterrole cluster-admin --serviceaccount=kube-system:tiller

clusterrolebinding.rbac.authorization.k8s.io/tiller created

clusterrolebinding.rbac.authorization.k8s.io/tiller created

helm init --service-account tiller --upgrade

helm repo update
```

# MongoDB

```helm install --name mongodb-demo stable/mongodb-replicaset
NAME:   mongodb-demo
LAST DEPLOYED: Wed May  1 18:54:51 2019
NAMESPACE: default
STATUS: DEPLOYED

RESOURCES:
==> v1/ConfigMap
NAME                                     DATA  AGE
mongodb-demo-mongodb-replicaset-init     1     1s
mongodb-demo-mongodb-replicaset-mongodb  1     1s
mongodb-demo-mongodb-replicaset-tests    1     1s

==> v1/Pod(related)
NAME                               READY  STATUS   RESTARTS  AGE
mongodb-demo-mongodb-replicaset-0  0/1    Pending  0         1s

==> v1/Service
NAME                                    TYPE       CLUSTER-IP  EXTERNAL-IP  PORT(S)    AGE
mongodb-demo-mongodb-replicaset         ClusterIP  None        <none>       27017/TCP  1s
mongodb-demo-mongodb-replicaset-client  ClusterIP  None        <none>       27017/TCP  1s

==> v1/StatefulSet
NAME                             READY  AGE
mongodb-demo-mongodb-replicaset  0/3    1s


NOTES:
1. After the statefulset is created completely, one can check which instance is primary by running:

    $ for ((i = 0; i < 3; ++i)); do kubectl exec --namespace default mongodb-demo-mongodb-replicaset-$i -- sh -c 'mongo --eval="printjson(rs.isMaster())"'; done

2. One can insert a key into the primary instance of the mongodb replica set by running the following:
    MASTER_POD_NAME must be replaced with the name of the master found from the previous step.

    $ kubectl exec --namespace default MASTER_POD_NAME -- mongo --eval="printjson(db.test.insert({key1: 'value1'}))"

3. One can fetch the keys stored in the primary or any of the slave nodes in the following manner.
    POD_NAME must be replaced by the name of the pod being queried.

    $ kubectl exec --namespace default POD_NAME -- mongo --eval="rs.slaveOk(); db.test.find().forEach(printjson)"
    
```
