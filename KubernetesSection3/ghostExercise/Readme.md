# PersistantVolume 10GB

set up Horizontal Pos Auto Scaler to scale with CPU at 50%
kubectlautoscale deployment ghost --cpu-percent=50 --min=1 --max=5
## Add local Volumes to yamls (see wordpress example)

```sh
    kubectl create -f local-volumes-ghost.yaml
    kubectl get persistentvolumes
    #kubectl apply -f ghost-mysql-deployment.yaml
    kubectl apply -f ghost-deployment.yaml
```