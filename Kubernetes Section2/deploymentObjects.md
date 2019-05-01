 kubectl get namespaces

#Deployment Objects
- Create
- Update
* Apply Rolling updates
* Roll back to previous version
* Pause & Resume


List
kubectl get deployments

### View status 
kubectl rollout status deployment namespace name

kubectl set image
ex. 
kubectl set image deployment/tomcat-deployment tomcat=tomcat:9.0.1
kubectl rollout history deployment/tomcat-deployment
```sh
 kubectl rollout history  -n encryptor deployment/encryptor-support-kube-state-metrics
deployments "encryptor-support-kube-state-metrics"
REVISION  CHANGE-CAUSE
1         <none>


$kubectl rollout history  -n encryptor deployment/encryptor-support-kube-state-metrics --revision=1
```


kubectl describe services -n streamer


[Health Checks](TomcatDeployment/HealthChecking.md)

