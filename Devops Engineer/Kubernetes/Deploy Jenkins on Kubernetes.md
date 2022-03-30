---
The Nautilus DevOps team is planning to set up a Jenkins CI server to create/manage some deployment pipelines for some of the projects. 
They want to set up the Jenkins server on Kubernetes cluster. Below you can find more details about the task:

1) Create a namespace jenkins

2) Create a Service for jenkins deployment. Service name should be jenkins-service under jenkins namespace, type should be NodePort, nodePort should be 30008

3) Create a Jenkins Deployment under jenkins namespace, It should be name as jenkins-deployment , labels app should be jenkins , container name should be jenkins-container , use jenkins/jenkins image , containerPort should be 8080 and replicas count should be 1.

Make sure to wait for the pods to be in running state and make sure you are able to access the Jenkins login screen in the browser before hitting the Check button

First check whether the namespace jenkins existed or not. If not create as below
```
kubectl create namespace jenkins
```
Write the below jenkins.yml file under /tmp folder
```
apiVersion: v1
kind: Service
metadata:
  name: jenkins-service
  namespace: jenkins
spec:
  type: NodePort
  selector:
    app: jenkins
  ports:
    - port: 8080
      targetPort: 8080
      nodePort: 30008

apiVersion: apps/v1
kind: Deployment
metadata:
  name: jenkins-deployment
  namespace: jenkins
  labels:
    app: jenkins
spec:
  replicas: 1
  selector:
    matchLabels:
      app: jenkins
  template:
    metadata:
      labels:
        app: jenkins
    spec:
      containers:
        - name: jenkins-container
          image: jenkins/jenkins
          ports:
            - containerPort: 8080
 ```
to check the running pods under jenkins namespace

```
kubectl get pods -n jenkins

kubectl exec jenkins-deployment-6b6c78f968-dtxcf -n jenkins -- curl http://localhost:8080

kubectl exec -n jenkins -- cat /var/jenkins_home/secrets/initialAdminPassword -- to view the password

kubectl exec jenkins-deployment-6b6c78f968-dtxcf -n jenkins -- curl --user admin:6f477bf70c7a49e78576b8c6e1a48993 http://localhost:8080
```
