# Labels and Selectors

Organize in human readable terms identify resources. 

key:value pairs
ex hostname 
ex. 3 nodes 
    One has an ssd 
    use a selector to tell deployment that app should only go on a node with ssd storage

Selectors: 
     make decisions and per 

     nodeSelector
     Label node as having an SSD
     Label node

     kubectl get nodes

kubectl label node minikube storageType=ssd


## UPdate Labels with deployment.yml
```yml
Add to yml:
  nodeSelector:
        storageType: ssd
```
```sh
kubectl apply -f ./deployment.yaml 
```

