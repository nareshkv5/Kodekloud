
We have an application running on Kubernetes cluster using nginx web server. The Nautilus application development team has pushed some of the latest changes 
and those changes need be deployed. The Nautilus DevOps team has created an image nginx:1.18 with the latest changes.

Perform a rolling update for this application and incorporate nginx:1.18 image. The deployment name is nginx-deployment

Make sure all pods are up and running after the update.

Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.

Run the below commands and check the deployment file
```
kubectl describe deploy nginx-deployment
```
You need to edit the image in the deploy file by edit directly the deployment file as below
```
kubectl edit deploy nginx-deployment and update the image name to nginx:1.18
````
#### or
```
kubectl set image deployment nginx-deployment nginx-container=nginx:1.18
```
Check the pods should be up and running. Here they given 3 replicas so three pods should be up and running. 

kubectl describe deploy nginx-deployment -- to view the changes reflecting or not.
kubectl get deploy -- to view the deployment file running with how many pods

#### to view whether the deployment rolled out successfully or not.
```
kubectl rollout status deployment nginx-deployment
```
