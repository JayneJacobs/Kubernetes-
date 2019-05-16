

Kubelet - Runs Pods
kube-proxy service: loadbalancer

## Scaling
ethier of the following
1. Set replicas = 4 and restart
2. use kubectl scale

```sh
kubectl scale --replicas=4 deployment/tomcat-deployment

 kubectl scale --replicas=4 deployment/tomcat-deployment
deployment.extensions/tomcat-deployment scaled
$ kubectl get deployment
NAME                READY   UP-TO-DATE   AVAILABLE   AGE
hazelcast           1/1     1            1           16h
tomcat-deployment   4/4     4            4           23h
$ kubectl edit deployment tomcat-deployment

$ kubectl get deployment tomcat-deployment
Conditions:
  Type           Status  Reason
  ----           ------  ------
  Progressing    True    NewReplicaSetAvailable
  Available      True    MinimumReplicasAvailable
OldReplicaSets:  <none>
NewReplicaSet:   tomcat-deployment-5c4b9b9c99 (4/4 replicas created)
Events:
  Type    Reason             Age    From                   Message
  ----    ------             ----   ----                   -------
  Normal  ScalingReplicaSet  5m21s  deployment-controller  Scaled up replica set tomcat-deployment-5c4b9b9c99
  ```

![Image](KubernetesContainers.png)
  Multiple nodes, need to expose more than a single port
  # Load Balancer
Exposes a single port to the client
Uses internal logic to decide which pod to send the request to. 

kubectl expose deployment tomcat-deployment --type=NodePort

### Load balancer service:
```sh
kubectl expose deployment tomcat-deployment --type=LoadBalancer --port=8080 --target-port=8080 --name tomcat-load-balancer
            service/tomcat-load-balancer exposed
kubectl describe services tomcat-load-balancer
kubectl scale --replicas=4 deployment/tomcat-deployment 
 
kubectl expose deployment tomcat-deployment --type=NodePort
kubectl expose deployment tomcat-deployment --type=LoadBalancer --port=8080 --target-port=8080 --name tomcat-load-balancer
 
kubectl describe services tomcat-load-balancer
```

### Alternative Method
549  git clone https://github.com/kubernetes/charts.git
  550  ls
  551  cd charts
  552  ls
  553  cd stable
  554  ls
  555  cd mongodb
  556  ls
  557  helm install --name mongodb-demo stable/mongodb
  558  cd ../mongodb-replicaset/
  559  ls
  560  helm install --name mongodb-demo .

![Image](../Docker/dockerapp/ContainerLinks.png)