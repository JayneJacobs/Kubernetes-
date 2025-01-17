kubectl create secret generic db-user-pass --from-file=./username.txt --from-file=./password.txt

kubectl create secret generic mysql-pass --from-literal=password=NEW_PASSWORD
kubectl get secret
 
kubectl apply -f mysql-deployment.yaml
kubectl apply -f wordpress-deployment.yaml
minikube service wordpress --url

Trouble Shooting
Error 1

If the wordpress pods keeps restarting until it gets a CrashLoopBackOff error.  The logs of the wordpress have the below error. 

MySQL Connection Error: (1045) Access denied for user 'root' (using password:YES)
Warning: mysqli::mysqli(): (HY000/1045): Access denied for user 'root' (using password:YES) in - on line 22
It means  WORDPRESS_DB_PASSWORD is not set up for wordpress pod correctly. We have noticed this weird issue, that the old secret we set in the previous lecture doesn't get updated in this lecture.

Solution:

solution is when you run the below kubectl create secret command, you pass the old secret used in the previous lecture, this will keep a lot of permission issues from occurring, so that you can follow along.  (credits given to @Brian)

kubectl create secret generic mysql-pass --from-literal=password=NEW_PASSWORD


Error 2

The Deployment "wordpress-mysql" is invalid: spec.template.spec.containers[0].env[0].valueFrom: Invalid value: "": may not be specified when `value` is not empty
In some versions of k8s tools when moving from a variable-based declaration to a secret-backed declaration the deployments must be deleted. 

Solution:

run the below commands to  delete all the resources, restart minikube, then retry the commands.

kubectl delete -f ./mysql-deployment.yaml
kubectl delete -f ./wordpress-deployment.yaml
minikube stop
minikube start
kubectl apply -f ./mysql-deployment.yaml
kubectl apply -f ./wordpress-deployment.yaml
