-----
The Nautilus DevOps teams is planning to set up a Grafana tool to collect and analyze analytics from some applications. They are planning to deploy it on Kubernetes cluster. Below you can find more details.



1.) Create a deployment named grafana-deployment-xfusion using any grafana image for Grafana app. Set other parameters as per your choice.

2.) Create NodePort type service with nodePort 32000 to expose the app.

You need not to make any configuration changes inside the Grafana app once deployed, just make sure you are able to access the Grafana login page.

Note: The kubeclt on jump_host has been configured to work with kubernetes cluster.

- kubectl get pods 
- kubectl get service
- Post that create grafana.yaml in tmp folder as below. Yaml code attached in separate file.
- vi /tmp/grafana.yaml
- cat /tmp/grafana.yaml
- kubectl create -f /tmp/grafana.yaml
- kubectl get service
- kubectl get pods make sure the pod are in running status.
- Just click grafana icon on the top right to view the grafana running status.
- Further your task is finished. Please click on check and finish the task
