
### Auto-Scaling

Kubernettes Course Section 5, Lecture 57
### Commands

(In the first terminal)
Create an HPA - Horizontal Pod Scaler
Adjusts number of replicas of a Pod to match observed average CPU utilization to a specifiec target


# since the latest minikube doesn't enable metrics-server by default
minikube addons enable metrics-server  
 
kubectl apply -f ./wordpress-deployment.yaml
 # CREATE AUTOSCALER
kubectl autoscale deployment wordpress --cpu-percent=50 --min=1 --max=5
(In the other terminal)

kubectl run -i --tty load-generator --image=busybox --generator=run-pod/v1 /bin/sh
 
while true; do wget -q -O- http://wordpress.default.svc.cluster.local; done
Note: In the latest version of kubectl, using kubectl run with some generators except pods is deprecated. As consequence, we should specify the run-pod/v1 generator explicitly as below. For more information, take a look at https://kubernetes.io/docs/reference/kubectl/conventions/#generators

(In the first terminal)

kubectl get hpa


Trouble Shooting
In the other terminal where the load-generator is running, if it shows below errors

/ # while true ; do wget -q -O- http://wordpress.default.svc.cluster.local ; done
wget: can't connect to remote host (10.XX.XXX.XXX): Network is unreachable
wget: can't connect to remote host (10.XX.XXX.XXX): Network is unreachable
wget: can't connect to remote host (10.XX.XXX.XXX): Connection timed out
wget: can't connect to remote host (10.XX.XXX.XXX): Network is unreachable
wget: can't connect to remote host (10.XX.XXX.XXX): Connection timed out
Solution:

replace http://wordpress.default.svc.cluster.local with the output of minikube service wordpress --url

For example:

while true ; do wget -q -O- http://192.168.99.100:32094 ; done

Related Q&A:

https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/questions/4400548

https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/questions/4838588