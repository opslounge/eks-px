# Steps to deploy Portworx on EKS 

## Download eksctl
```
wget https://github.com/weaveworks/eksctl/releases/download/0.45.0/eksctl_Linux_amd64.tar.gz
```

## Install eksctl 
```
gunzip eksctl_Linux_amd64.tar.gz
untar -xvf eksctl_Linux_amd64.tar
cp eksctl /usr/bin
```
## Create Cluster Config using cluster config file
```
eksctl create cluster -f createcluster.yaml
```
## Deploy Operator
```
kubectl create -f https://install.portworx.com/?comp=pxoperator
```
## Deploy Portworx cluster
```
kubectl apply -f `https://install.portworx.com/2.6?mc=false&kbver=1.17.17-eks-c5067d&b=true&s=%22type%3Dgp2%2Csize%3D20%22&kd=type%3Dgp2%2Csize%3D150&c=px-cluster-66127310-f60c-4158-a7b0-feca11b877ff&eks=true&stork=true&st=k8s&e=ENABLE_ASG_STORAGE_PARTITIONING%3Dtrue`
```

## Create Storage Class
```
kubectl create -f storagecluster.yaml
```


