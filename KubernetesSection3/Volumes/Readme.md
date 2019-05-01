Cloud Providers

SAN/File system/Hardware

Specifying Volumes
     spec.volumes
     spec.containers
     
```sh
kubectl delete persistentvolumes  local-pv-2
```
Volumes separate stateles portions from stateful data. 

    scale, maintaine and separate app from data

    Ease portability baskup recovery. 

    Persistant volume

            disk-like
            Provision  as installing a disk. 

    Kube examines resources to define volumes

    Directories
    K8/dev cliaim volume.  K8 master matches to available volumes. 

    dynamic- creates new volumes as needed. 

    PersistantVolume object. 
    min/max
    read write/once

    path on the host. 

    SAN/NFS - 


    Claim Volume
    PersistentVolumeClaim
    k8 binds claim to volume or error

### Add local Volumes to yamls (see wordpress example )

```sh
    kubectl create -f local-volumes.yaml
    kubectl get persistentvolumes

    kubectl apply -f mysql-deployment.yaml
    kubectl apply -f wordpress-deployment.yaml

```
There is a newer version of minikube available (v1.0.0).  Download it here:
https://github.com/kubernetes/minikube/releases/tag/v1.0.0

To disable this notification, run the following:
minikube config set WantUpdateNotification false
http://192.168.99.100:30634


minikube service wordpress --url
kubectl get pods
kubectl get services --all-namespaces


kubectl create -f  local-volumes.yaml

kubectl apply -f mysql-deployment.yaml
kubectl apply -f wordpress-deployment.yaml
minikube service wordpress --url
kubectl delete -f ./mysql-deployment.yaml
kubectl delete -f ./wordpress-deployment.yaml
minikube stop
minikube start