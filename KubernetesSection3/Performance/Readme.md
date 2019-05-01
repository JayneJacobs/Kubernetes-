

# Usage and resources

* Heapster 
* InfluxDB
* Grafana

Heapster
    CNCF Project
    Gathers information on each pod by referencing kubelett
    Gets data from cadvisor / kubernettes component
    Sends information to influxDB. 
    Read by Grafana

    Enabled by default

    heapster computes resource usage

### Commands
    minikube addons enable heapster
    kubectl get pods --namespace=kube-system
    minikube addons open heapster

### Heapster Functionality
       Kubernettes Container Cluster Monitoring

       Maintained by CNCF

       