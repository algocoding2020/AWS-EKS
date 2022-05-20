# AWS-EKS
NPC

Node  > Pod > Container

Each POD has a unique IP address

One APP Container per Pod

The pod contains more than one container

Deploy object  > Replica Set > Pod
To run deployment 
-----------------
kubectl get all

kubectl get nodes

kubectl apply -f  nginx-deployment.yaml

kubectl get all

kubectl delete pod <name-of-the-pod>
  
kubectl get rs
  
//rs stands for replicaset
  
kubectl delete rs <name-of-the-rs>
  
kubectl get rs
  
kubectl describe pods
  
kubectl describe rs
  
kubectl describe deployment
  

Service Object > Cluster IP> NodePort > Loadbalancer
-----------------------------------------------------
-----------------------------------------------------
  
  The moto of all the service types is to discover and distribute the traffic to underlying pods

The default service is cluster IP .don;t mention type in manifest

cluster IP:
---------------

accessible within the cluster

clsuter IP manifest:

apiVersion: v1
kind: Service
metadata:
  name: app-service
spec:
  ports:
    - port: 80
      protocol: TCP
  selector:
    app: app-server
other pods use port 90 to access this service

it is a suitable app to DB traffic

Node port:
----------

Accessible from outside cluster

nodeport : accessible from the outside cluster

port: actual node port service is running

targetport: forward the traffic to port

Nodeport is exposed to all nodes in the cluster

Ex:

you have two nodes with IP

10.16.10.01

10.18.10.01

https://10.16.10.01:3200

traffic will be distributed to two nodes

Loadbalancer:
------------

Cloud Specific Implementation,Accessible from outside cluster

commnads:
eksctl get cluster

kubectl apply -f loadbalancer-service.yaml

kubectl get service

kubectl describe service <name-of-the-service>
  
EKSCTL> Cluster Creation

eksctl create cluster --name <name-of-the-cluster> --version 1.15 --nodegroup-name <nodegroupname> --node-type t3.micro --nodes 2 --manged
above commands create cluster with 2 nodes of type managed
then
kubectl apply -f nginx-deployment.yaml
it will create pod with nginx containers
