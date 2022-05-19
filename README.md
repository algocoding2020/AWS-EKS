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
