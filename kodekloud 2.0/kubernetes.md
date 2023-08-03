<h2>Create a ReplicSet in Kubernetes Cluster</h2>
Q) The Nautilus DevOps team is going to deploy some applications on kubernetes cluster as they are planning to migrate some of their existing applications there. Recently one of the team members has been assigned a task to write a template as per details mentioned below:

Create a ReplicaSet using nginx image with latest tag only and remember to mention tag i.e nginx:latest and name it as nginx-replicaset.
Labels app should be nginx_app, labels type should be front-end.
The container should be named as nginx-container; also make sure replicas counts are 4.

Create a replicaset as below by creating an yaml file.
```
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: nginx-replicaset
  labels:
    app: nginx_app
    type: front-end
spec:
  replicas: 4
  selector:
    matchLabels:
      app: nginx_app
  template:
    metadata:
      labels:
        app: nginx_app
    spec:
      containers:
      - image: nginx:latest
        name: nginx-container
```


<h2>Create Namespace in Kubernetes Cluster</h2>
Q) The Nautilus DevOps team is planning to deploy some micro services on Kubernetes platform. The team has already set up a Kubernetes cluster and now they want set up some namespaces, deployments etc. Based on the current requirements, the team has shared some details as below:
Create a namespace named dev and create a POD under it; name the pod dev-nginx-pod and use nginx image with latest tag only and remember to mention tag i.e nginx:latest.
Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.

First create namespace by using the below command
```
kubectl create ns dev
kubectl run dev-nginx-pod --image=nginx:latest -n dev
```
Q) The system admins team of xFusionCorp Industries has set up a new tool on all app servers, as they have a requirement to create a service user account that will be used by that tool.
Create a user named siva in App Server 1 without a home directory.

ssh to stapp1 server and use the below command to check the user first and then create the user

```
cat /etc/passwd | grep siva
sudo useradd -M siva
```
<h2>Set Limites for Resources in Kubernetes</h2>
Q) Recently some of the performance issues were observed with some applications hosted on Kubernetes cluster. The Nautilus DevOps team has observed some resources constraints, where some of the applications are running out of resources like memory, cpu etc., and some of the applications are consuming more resources than needed. Therefore, the team has decided to add some limits for resources utilization. Below you can find more details.

Create a pod named httpd-pod and a container under it named as httpd-container, use httpd image with latest tag only and remember to mention tag i.e httpd:latest and set the following limits:
Requests: Memory: 15Mi, CPU: 100m
Limits: Memory: 20Mi, CPU: 100m

Please create pod first with the mentioned requirements
```
kubectl run httpd-pod --image=httpd:latest --dry-run=client -oyaml > pod.yaml
```

The above one will create a pod post which you have to add the container name httpd-container and give the resources limit block under resources
```
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
```
<h2>Rolling Updates in Kubernetes</h2>
Q) We have an application running on Kubernetes cluster using nginx web server. The Nautilus application development team has pushed some of the latest changes and those changes need be deployed. The Nautilus DevOps team has created an image nginx:1.18 with the latest changes.
Perform a rolling update for this application and incorporate nginx:1.18 image. The deployment name is nginx-deployment
Make sure all pods are up and running after the update.
Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.

Please make sure you edit the deployment file and update the image version. Or we can use below command
```
kubectl set image deployment nginx-deployment nginx=nginx:1.14.2 --record
kubectl edit deployment nginx-deployment --record
```
Edit the image version and changes are applied automatically as above


<h2>Rollback a deployment in Kubernetes</h2>
Q) This morning the Nautilus DevOps team rolled out a new release for one of the applications. Recently one of the customers logged a complaint which seems to be about a bug related to the recent release. Therefore, the team wants to rollback the recent release.
There is a deployment named nginx-deployment; roll it back to the previous revision.
Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.

```
kubectl rollout undo deployment nginx-deployment -->This will move to previous deployment
kubectl rollout history deployment nginx-deployment -- will shows the deployment history
kubectl rollout --help will show the options for rollout
```

<h2>Create Deployments in Kubernetes Cluster</h2>
Q) The Nautilus DevOps team has started practicing some pods, and services deployment on Kubernetes platform, as they are planning to migrate most of their applications on Kubernetes. Recently one of the team members has been assigned a task to create a deploymnt as per details mentioned below:

Create a deployment named nginx to deploy the application nginx using the image nginx:latest (remember to mention the tag as well)

Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.

```
kubectl create deployment nginx --image=nginx:latest 
```
<h2>25/07/2023 - Create groups and add users under that group</h2>

Q)There are specific access levels for users defined by the xFusionCorp Industries system admin team. Rather than providing access levels to every individual user, the team has decided to create groups with required access levels and add users to that groups as needed. See the following requirements:

a. Create a group named nautilus_admin_users in all App servers in Stratos Datacenter.

b. Add the user kano to nautilus_admin_users group in all App servers. (create the user if doesn't exist).

Need to ssh in all app servers and create group first and then add the user as below 
```
getent group -- to view the existing groups

sudo groupadd nautilus_admin_users 

sudo useradd -g nautilus_admin_users kano
```

