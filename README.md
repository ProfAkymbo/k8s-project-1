## K8s manifest for myportfolio dockerized app using eksctl
use this command to create cluster
```
eksctl create cluster --name cluster-1 --nodegroup-name ng-1 --region us-east-1 --node-type t2.micro --nodes 2
```
You can verify that the cluster is running by using:
```
eksctl get cluster --name cluster-1 --region us-east-1
```
Let's list all the Pods in the cluster:
```
kubectl get pods --all-namespaces
```
we can deploy our manifest file with
```
kubectl apply -f deployment.yaml
```
To see if your application runs correctly, you can connect to it with kubectl port-forward.

First, retrieve the name of the Pod:
```
kubectl get pods
```
You can connect to the Pod with:
```
kubectl port-forward <output of pod name> 8080:8080
```
The command Connects to the Pod with the name of the pod.
Forwards all the traffic from port 8080 on the Pod to port 8080 on your computer.
If you visit http://localhost:8080 on your computer, you should be greeted by the application.
Great!

Exposing the application with kubectl port-forward is an excellent way to test the app quickly, but it isn't a long term solution.
the cluster can be deleted using
```
eksctl delete cluster --name cluster-1 --region us-east-1
```
