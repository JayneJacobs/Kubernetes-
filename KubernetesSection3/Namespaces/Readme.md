## Namespaces 
Section 5, Lecture 55
Commands For Cut & Paste

kubectl create namespace <namespace name>
kubectl create namespace <namespace name>
kubectl get namespace
kubectl create namespace cpu-limited-tomcat
Resource Quotas Commands
Example  CPU (200m per container with 3 replicas- 600m) in a namespacer with 400m. 

1. Create namespace
2. Assign 400m CPU resource limit
3. Deploy Tomcat into namespace with 3 replicax
4. Use kubectl to examine status. 


kubectl create -f ./cpu-limits.yaml —namespace=cpu-limited-tomcat (from the GitHub repo directory for this lecture)
kubectl apply -f ./tomcat-deployment.yaml —namespace=cpu-limited-tomcat (from the GitHub repo directory for this lecture)
kubectl describe deployment tomcat-deployment —namespace=cpu-limited-tomcat

kubectl autoscale deployment tomcat-deployment -n cpu-limited-tomcat --cpu-percent=50 --min=1 --max=5