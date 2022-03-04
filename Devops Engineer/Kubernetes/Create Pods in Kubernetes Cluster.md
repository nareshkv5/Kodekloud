----
The Nautilus DevOps team has started practicing some pods and services deployment on Kubernetes platform as they are planning to migrate most of their applications 
on Kubernetes platform. Recently one of the team members has been assigned a task to create a pod as per details mentioned below:

Create a pod named pod-httpd using httpd image with latest tag only and remember to mention the tag i.e httpd:latest.

Labels app should be set to httpd_app, also container should be named as httpd-container.

The pod created as per the instruction provided, please find the below
---

```
apiVersion: v1
kind: Pod
metadata:
  name: pod-httpd
  labels:
    app: httpd_app
spec:
  containers:
    - name: httpd-container
      image: httpd:latest
```

