
Q) The Nautilus DevOps team is planning to deploy some micro services on Kubernetes platform. The team has already set up a Kubernetes cluster and now they want set up some namespaces, deployments etc. Based on the current requirements, the team has shared some details as below:
Create a namespace named dev and create a POD under it; name the pod dev-nginx-pod and use nginx image with latest tag only and remember to mention tag i.e nginx:latest.
Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.

First create namespace by using the below command

kubectl create ns dev

---kubectl run dev-nginx-pod --image=nginx:latest -n dev


Q) The system admins team of xFusionCorp Industries has set up a new tool on all app servers, as they have a requirement to create a service user account that will be used by that tool.
Create a user named siva in App Server 1 without a home directory.

ssh to stapp1 server and use the below command to check the user first and then create the user

--cat /etc/passwd | grep siva

--sudo useradd -M siva


Recently some of the performance issues were observed with some applications hosted on Kubernetes cluster. The Nautilus DevOps team has observed some resources constraints, where some of the applications are running out of resources like memory, cpu etc., and some of the applications are consuming more resources than needed. Therefore, the team has decided to add some limits for resources utilization. Below you can find more details.


Q) Create a pod named httpd-pod and a container under it named as httpd-container, use httpd image with latest tag only and remember to mention tag i.e httpd:latest and set the following limits:

Requests: Memory: 15Mi, CPU: 100m

Limits: Memory: 20Mi, CPU: 100m

Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.

-- Please create pod first with the mentioned requirements
-- kubectl run httpd-pod --image=httpd:latest --dry-run=client -oyaml > pod.yaml 

The above one will create a pod post which you have to add the container name httpd-container and give the resources limit block under resources

apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: httpd-pod
  name: httpd-pod
spec:
  containers:
  - image: httpd:latest
    name: httpd-container
    resources:
      requests:
        memory: "15Mi"
        cpu: "100m"
      limits:
        memory: "20Mi"
        cpu: "100m"


Q) We have an application running on Kubernetes cluster using nginx web server. The Nautilus application development team has pushed some of the latest changes and those changes need be deployed. The Nautilus DevOps team has created an image nginx:1.18 with the latest changes.
Perform a rolling update for this application and incorporate nginx:1.18 image. The deployment name is nginx-deployment
Make sure all pods are up and running after the update.
Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.

Please make sure you edit the deployment file and update the image version. Or we can use below command

kubectl set image deployment nginx-deployment nginx=nginx:1.14.2 --record

kubectl edit deployment nginx-deployment --record     -- Edit the image version and changes are applied automatically

Q) This morning the Nautilus DevOps team rolled out a new release for one of the applications. Recently one of the customers logged a complaint which seems to be about a bug related to the recent release. Therefore, the team wants to rollback the recent release.
There is a deployment named nginx-deployment; roll it back to the previous revision.
Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.

-- kubectl rollout undo deployment nginx-deployment -- This will move to previous deployment

-- kubectl rollout history deployment nginx-deployment -- will shows the deployment history

-- kubectl rollout --help will show the options for rollout


