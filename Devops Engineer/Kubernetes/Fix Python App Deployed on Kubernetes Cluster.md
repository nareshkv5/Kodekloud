One of the DevOps engineers was trying to deploy a python app on Kubernetes cluster. Unfortunately, due to some mis-configuration, the application is not coming up. 
Please take a look into it and fix the issues. Application should be accessible on the specified nodePort.

The deployment name is python-deployment-datacenter, its using poroko/flask-demo-app image. The deployment and service of this app is already deployed.

nodePort should be 32345 and targetPort should be python flask app's default port.

Note: The kubectl on jump_host has been configured to work with the kubernetes cluster.

#### Run kubectl get po to check the pods
```
kubectl describe deploy
```
kubectl edit deploy edit the project name to flask-demo-app instead of flask-app-demo

Now check the services running by below command
```
kubectl get svc
kubectl get deploy && kubectl get pods
```
Wait for the deployment file and pod it should be running
Now edit the service file
```
kubectl edit svc
```
Change the port to 5000 (default port id of python flask)
By clicking on app you can validate the changes and see output as helloworld
