
One of the Nautilus DevOps team members was working on to update an existing Kubernetes template. 
Somehow, he made some mistakes in the template and it is failing while applying. We need to fix this as soon as possible, 
so take a look into it and make sure you are able to apply it without any issues. Also, do not remove any component 
from the template like pods/deployments/volumes etc.

/home/thor/mysql_deployment.yml is the template that needs to be fixed.

Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.

Please check first all the resources or objects with below command
```
kubectl get all
```
And then try to create the deployment and check we will come to know the errors.
```
kubectl create -f mysql_deployment.yml
```
There were issues with PV object and pvc object where apiVersion is mentioned wrongly need to correct that. And the size 250Mi is mentioned as 250MB in pvc claim object need to correct that as well. Like this there are indentation issues have attached the wrong yaml file and validated yaml. Please find
