---------------------------------------------------------------------------------------------------------------------------------------------
28/Jan/2022 -- Countdown job in Kubernetes
---------------------------------------------------------------------------------------------------------------------------------------------

The Nautilus DevOps team is working on to create few jobs in Kubernetes cluster. They might come up with some real scripts/commands to use, 
but for now they are preparing the templates and testing the jobs with dummy commands. Please create a job template as per details given below:

Create a job countdown-xfusion.

The spec template should be named as countdown-xfusion (under metadata), and the container should be named as container-countdown-xfusion

Use image ubuntu with latest tag only and remember to mention tag i.e ubuntu:latest, and restart policy should be Never.

Use command for i in 10 9 8 7 6 5 4 3 2 1 ; do echo $i ; done

Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.

kubectl get deploy -A

kubectl get pods

#### vi /tmp/countdown.yaml

```
apiVersion: batch/v1
kind: Job
metadata:
  name: countdown-xfusion
spec:
  template:
    metadata:
      name: countdown-xfusion
    spec:
      containers:
        - name: container-countdown-xfusion
          image: ubuntu:latest
          command: ["/bin/sh", "-c"]
          args:
            [
              "for i in 10 9 8 7 6 5 4 3 2 1 ; do echo $i ; done",
            ]
      restartPolicy: Never
```
kubectl create -f /tmp/countdown.yaml 

kubectl get pods -- check after pod status is completed

Check logs now.

kubectl logs pod_name -- It will pring 10 9 8 and a

[link to check the above command](https://askubuntu.com/questions/831847/what-is-the-sh-c-command)
