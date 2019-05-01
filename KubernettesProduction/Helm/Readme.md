# Helm


Stefan Thorpe will talk you through one of the most popular package managers for Kubernetes, Helm.

Through a series of of lectures, you would see Helm helps to manage Kubernetes applications: Helm Charts helps you define, install, and upgrade even the most complex Kubernetes application.

Stefan Thorpe is a certified cloud architect and has decades of experience in both cloud computing and DevOps industry.

Simple way to package and configure.  in on deployment. 

Do not repeat coding principles 

configure a package and manage dependencies. 

Update and remove containers. 

Define run, upgrade for public distribution. 


## Helm Charts: 
 Kubernettes Yamls. 

 helm/tiller runs on Kubernetes clusters. 

 Helm sends charts to Tiller Server.  and tiller installs the package. 

Tiller comiles yamls and applies them to cluster. 

Single CLI command line. 

Helm tool; 
 Package description (yaml)
 Templates: Yaml files

 Accessign Helm Charts. 
  repository
  Helm install; location of charts; chart name. 

  Charts define, run , upgrade. 

  official and unoffficial charts. 

  install helm. 

 Google Cloud account/project
 Gcloud SDK

## Setup Tiller

```sh
kubectl delete clusterrolebinding tiller
 kubectl create clusterrolebinding tiller --clusterrole cluster-admin --serviceaccount=kube-system:tiller
 helm install --name mongodb-demo stable/mongodb-replicaset

clusterrolebinding.rbac.authorization.k8s.io/tiller created

helm init --service-account tiller --upgrade
    
 helm repo update
```
#Repair

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
