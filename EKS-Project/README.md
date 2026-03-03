# AWS EKS Commands:

## Build & Push Docker Image

```sh
docker image build -t thiernos/eks-app:1.0 .

docker container run -dp 3000:3000 --name eks-app thiernos/eks-app:1.0
```

## Configure eksctl (EKS CLI created by Weaveworks)

```sh
brew tap weaveworks/tap
brew install weaveworks/tap/eksctl
```

```sh
eksctl version
```

## Crete a Cluster

```sh
eksctl create cluster \
 --name eks-cluster \
 --version 1.29 \
 --region eu-west-3 \
 --nodegroup-name eks-workers \
 --node-type t3.micro \
 --nodes 3 \
 --nodes-min 1 \
 --nodes-max 4 \
 --managed
```

```sh
eksctl get cluster
```

## Create a Deployment on the EKS Cluster:

```sh
aws eks update-kubeconfig --name eks-cluster --region eu-west-3
```

```sh
kubectl apply -f app-server-deployment.yaml
kubectl get all
kubectl get pods
kubectl get nodes
```

## Cleanup

```sh
eksctl delete cluster --name eks-cluster
```

## Test Deployment:

```sh
kubectl get all
```

## Copy LoadBalacner Endpoint

```sh
http://YOUR_LOAD_BALANCER_ENDPOINT:3000/contacts
```
