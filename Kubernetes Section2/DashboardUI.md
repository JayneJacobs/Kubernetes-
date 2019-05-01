

#Dashboard Web UI

proxy/tunel to start UI
$ kubectl proxy
Update, delete, create
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v1.10.1/src/deploy/recommended/kubernetes-dashboard.yaml


Installing
kubectl create -f 

http://localhost:8001/ui



http://localhost:8001/api/v1/namespaces/kube-system/services/http:kubernetes-dashboard:/proxy/#!/overview?namespace=default


