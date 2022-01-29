---------------------------------------------------------------------------------------------------------------------------------------------
24/Jan/2022 -- Create Namespaces in Kubernetes Cluster
---------------------------------------------------------------------------------------------------------------------------------------------

The Nautilus DevOps team is planning to deploy some micro services on Kubernetes platform. The team has already set up a Kubernetes cluster and now they want set up some namespaces, deployments etc. Based on the current requirements, the team has shared some details as below:

Create a namespace named dev and create a POD under it; name the pod dev-nginx-pod and use nginx image with latest tag only and remember to mention tag i.e nginx:latest.

Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.


 #### kubectl get namespace --- to view the existing namespace

 #### kubectl create namespace dev -- to create a dev namespace as per the task

-- creating a pod with image (nginx:latest) nginx and tag as latest under namespace dev

```
kubectl run dev-nginx-pod --namespace=dev --image=nginx:latest (or) kubectl run dev-nginx-pod --image=nginx:latest -n dev
```
To check which pods are running under any namespaces

 #### kubectl get pods -n dev 

kubectl describe po dev-nginx-pod -n dev -- to view the complete details of pod verify the image and podname and finish the task
