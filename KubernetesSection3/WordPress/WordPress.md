# DNS & Service Discovery

### syntax of the [deployment](https://github.com/jleetutorial/kubernetes-demo/tree/master/Advanced%20Kubernetes%20Usage/DNS%20and%20Service%20Discovery) 


files and kubectl commands


# Introduction to YAML: Creating a Kubernetes deployment



#### [Api Version](https://github.com/jleetutorial/kubernetes-demo/blob/master/Advanced%20Kubernetes%20Usage/DNS%20and%20Service%20Discovery/mysql-deployment.yaml#L15)
'---' is used for separating documents. 

#### [Place multiple things in a single file ](https://github.com/jleetutorial/kubernetes-demo/blob/master/Advanced%20Kubernetes%20Usage/DNS%20and%20Service%20Discovery/mysql-deployment.yaml#L15)

- e.g. services, deployments, etc. We could have made separate documents. 

One for service, one for deployment, but the '---' allows us placing them in a single file.

[Which api Version to use?](https://matthewpalmer.net/kubernetes-app-developer/articles/kubernetes-apiversion-definition-guide.html)

Difference between kubectl create and kubectl apply : kubectl create can be used only for creating new deployments; kubectl apply can be used for both creating and updating deployments. Other than that they're pretty much identical.