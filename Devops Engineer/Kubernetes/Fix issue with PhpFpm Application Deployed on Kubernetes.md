----
We deployed a Nginx and PHPFPM based application on Kubernetes cluster last week and it had been working fine. This morning one of the team members was 
troubleshooting an issue with this stack and he was supposed to run Nginx welcome page for now on this stack till issue with phpfpm is fixed but he made a 
change somewhere which caused some issue and the application stopped working. Please look into the issue and fix the same:

The deployment name is nginx-phpfpm-dp and service name is nginx-service. Figure out the issues and fix them. 
FYI Nginx is configured to use default http port, node port is 30008 and copy index.php under /tmp/index.php to deployment under /var/www/html. 
Please do not try to delete/modify any other existing components like deployment name, service name etc.

Note: The kubectl utility on jump_host has been configured to work with the kubernetes cluster.

Lets check the existing service file/configmap/pods/deployment etc by using the below commands.
```
kubectl get pods
kubectl describe pod 
kubectl get deploy
kubectl get svc
kubectl get configmap
kubectl logs nginx-phpfpm-dp-5cccd45499-hmgfp -c php-fpm-container
```
-- To check the logs of pod for a specific container since there are two container used one is nginx-container other is php-fpm-container.

-- If you notice in configmap nginx port is set to default 80. As per task nginx port is using default so edit the service and modify the port of nginx from 8092 
   to default 80.

ttp {
  server {
    listen 80 default_server;
    listen [::]:80 default_server;

    # Set nginx to serve files from the shared volume!
    root /var/www/html;
    index  index.html index.ph p index.htm;
    server_name _;
    location / {
      try_files $uri $uri/ =404;
    }
    location ~ \.php$ {
      include fastcgi_params;
      
      
 -- To edit the service and change the port number of nginx service to 80 where ever 8091 is there use the below commands
 
 ```
 kubectl rollout restart deployment nginx-phpfpm-dp
 kubectl get svc
 kubectl edit service nginx-service
 ```
 --- Post changing check the changes whether it's reflecting or not.
 
 -- copy php file in nginx container as per the task
 
 ```
 kubectl cp /tmp/index.php nginx-phpfpm-dp-5cccd45499-hmgfp:/var/www/html -c nginx-container
 ```
 
 --- Login to nginx-container and check whether index.php file is copied or not with the below command
 
 ```
 kubectl exec -it nginx-phpfpm-dp-5cccd45499-hmgfp -c nginx-container -- bash
 
 ```
 
