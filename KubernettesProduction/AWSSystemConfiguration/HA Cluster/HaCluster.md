# Delete cluster
kops delete cluster jayne-k8s-demo.k8s.local --yes

# Create HA Cluster
remember no spaces after commas
```sh
kops create cluster jayne-k8s-demo.k8s.local --zones us-east-2a,us-east-2b,us-east-2c --node-count 3 --master-zones us-east-2a,us-east-2b,us-east-2c --yes
```

# validate cluster

```sh 
kops validate cluster

Using cluster from kubectl context: jayne-k8s-demo.k8s.local

Validating cluster jayne-k8s-demo.k8s.local

INSTANCE GROUPS
NAME			ROLE	MACHINETYPE	MIN	MAX	SUBNETS
master-us-east-2a	Master	c4.large	1	1	us-east-2a
master-us-east-2b	Master	c4.large	1	1	us-east-2b
master-us-east-2c	Master	c4.large	1	1	us-east-2c
nodes			Node	t2.medium	3	3	us-east-2a,us-east-2b,us-east-2c

NODE STATUS
NAME						ROLE	READY
ip-172-20-110-238.us-east-2.compute.internal	node	True
ip-172-20-126-135.us-east-2.compute.internal	master	True
ip-172-20-51-242.us-east-2.compute.internal	master	True
ip-172-20-58-226.us-east-2.compute.internal	node	True
ip-172-20-75-74.us-east-2.compute.internal	master	True
ip-172-20-88-121.us-east-2.compute.internal	node	True

VALIDATION ERRORS
KIND	NAME					MESSAGE
Pod	kube-system/kube-dns-6b4f4b544c-g8nt9	kube-system pod "kube-dns-6b4f4b544c-g8nt9" is not healthy
Pod	kube-system/kube-dns-6b4f4b544c-g8nt9	kube-system pod "kube-dns-6b4f4b544c-g8nt9" is not healthy
Pod	kube-system/kube-dns-6b4f4b544c-g8nt9	kube-system pod "kube-dns-6b4f4b544c-g8nt9" is not healthy
Pod	kube-system/kube-dns-6b4f4b544c-j8r2r	kube-system pod "kube-dns-6b4f4b544c-j8r2r" is not healthy
Pod	kube-system/kube-dns-6b4f4b544c-j8r2r	kube-system pod "kube-dns-6b4f4b544c-j8r2r" is not healthy
Pod	kube-system/kube-dns-6b4f4b544c-j8r2r	kube-system pod "kube-dns-6b4f4b544c-j8r2r" is not healthy

Validation Failed
```
