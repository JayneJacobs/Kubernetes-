# AWS Kubernettes cluster configuration

1. Install kops
brew update && brew install kops
kops
2. Configure aws comandline tool
   curl -O https://bootstrap.pypa.io/get-pip.py
   python3 get-pip.py --user
    pip --version
    which python
  
    ls -al /usr/local/bin/python
    ls -a ~
    ls -a ~ | more
    vi .bash_profile
    alias python=python3
    alias pip=pip3
    export PATH=~/.local/bin:$PATH
    source ~/.bash_profile
Add credentials to aws CLI

         

3. Create aws s3 bucket as state store
    aws s3api create-bucket --bucket jayne-k8s-demo-bucket --region us-east-2 --create-bucket-configuration LocationConstraint=us-east-2
{
    "Location": "http://jayne-k8s-demo-bucket.s3.amazonaws.com/"
}
4. create the cluster with kops
set environment variable for location in bash_profile
 ssh-keygen
 ls
 chmod 400 id*
 ls -la
 kops create cluster jayne-k8s-demo.k8s.local --zones us-east-2a --yes
 kops validate cluster
 kubectl get nodes --show-labels

 #ssh into master

cat kube-apiserver.log
 kubectl get deployments --namespace=kube-system
#Trouble Shooting
Cluster is starting.  It should be ready in a few minutes.

Suggestions:
 * validate cluster: kops validate cluster
 * list nodes: kubectl get nodes --show-labels
 Get the master DNS name from the AWS console . Such as: https://us-east-2.console.aws.amazon.com/ec2/v2/home?region=us-east-2#Instances:sort=instanceId


 * ssh to the master: ssh -i ~/.ssh/id_rsa admin@ec2-18-191-186-43.us-east-2.compute.amazonaws.com
 
 * the admin user is specific to Debian. If not using Debian please use the appropriate user based on your OS.
 * read about installing addons at: https://github.com/kubernetes/kops/blob/master/docs/addons.md.

kops create cluster maranics-k8-demo1.k8.local --zones us-west-2a --yes
I0731 15:53:42.130448   41571 create_cluster.go:1318] Using SSH public key: /Users/xxp/.ssh/id_rsa.pub
I0731 15:53:43.957333   41571 create_cluster.go:472] Inferred --cloud=aws from zone "us-west-2a"
I0731 15:53:45.760687   41571 subnets.go:184] Assigned CIDR 172.20.32.0/19 to subnet us-west-2a
 
error determining default DNS zone: No matching hosted zones found for ".maranics-k8-demo1.k8.local"; please create one (e.g. "k8.local") first
Solution:

run below command instead.

kops create cluster cluster.k8s.local --zones us-west-2a --yes

Related Q&A:

https://www.udemy.com/kubernetes-from-a-devops-kubernetes-guru/learn/v4/questions/4825364


Get rid of the cluster so there 

kops delete cluster jayne-k8s-demo.k8s.local --yes
