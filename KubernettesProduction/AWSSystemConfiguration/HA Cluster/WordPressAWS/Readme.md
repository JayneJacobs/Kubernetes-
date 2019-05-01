# Deploy Application on AWS Kubernettes with HA


501  cd "/LocalDocuments/Training/ContainerTraining/KubernettesProduction/AWSSystemConfiguration/HA Cluster/WordPressAWS"
  502  kubectl apply -f ./mysql-deployment.yaml 
  503  kubectl apply -f ./wordpress-deployment.yaml 
  504  kubectl get pods
  505  kubectl describe pod
  506  kubectl describe pods
  507  kubectl describe service wordpress

# Create Volumes in AWS
kubectl delete deployment wordpress
kubectl delete deployment wordpress-mysq
echo $KOPS_STATE_STORE

kops create cluster jayne-k8s-demo.k8s.local --zones us-east-2a --yes

