## Auditing


Trouble Shooting:
If you hang running the script file on 'Starting cluster components'

minikube start  --extra-config=apiserver.Authorization.Mode=RBAC --extra-config=apiserver.Audit.LogOptions.Path=/var/logs/audit.log   --extra-config=apiserver.Audit.PolicyFile=/etc/kubernetes/addons/audit-policy.yaml


# cp audit-policy.yaml 

```sh
cp audit-policy.yaml ~/.minikube/addons/
kubectl get pods
minikube ssh
cat /var/log/audit.log | jq .
```

results in the command hanging on 'Starting cluster components...'

Starting local Kubernetes v1.10.0 cluster...
Starting VM...
Getting VM IP address...
Moving files into cluster...
Setting up certs...
Connecting to cluster...
Setting up kubeconfig...
Starting cluster components...
and the error log in minikube says

failed to run Kubelet: unable to load bootstrap kubeconfig: stat /etc/kubernetes/bootstrap-kubelet.conf: no such file or director

Solution:

This is an issue with minikube 0.28, there is a ticket open regarding this issue.

To walk around it, you can uninstall the current version of minikube and reinstall minikube 0.25.2

Related Q&A:

https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/questions/4555676

https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/questions/4471680