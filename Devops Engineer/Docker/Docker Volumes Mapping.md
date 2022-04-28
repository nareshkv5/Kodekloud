
The Nautilus DevOps team is testing applications containerization, which issupposed to be migrated on docker container-based environments soon. In today's stand-up meeting one of the team members has been assigned a task to create and test a docker container with certain requirements. Below are more details:

a. On App Server 2 in Stratos DC pull nginx image (preferably latest tag but others should work too).

b. Create a new container with name official from the image you just pulled.

c. Map the host volume /opt/security with container volume /usr/src/. There is an sample.txt file present on same server under /tmp; copy that file to /opt/security. Also please keep the container in running state.

Please login to app2 server as ssh steve@stapp02 and provide the password change to root user by using sudo su

As per the task we need to pull the nginx latest image as below
```
docker pull nginx-latest
```
As per the task we need to copy /tmp/sample.txt to /opt/security folder as below.
```
cp /tmp/sample.txt /opt/security/
```
ll /opt/security -- to check whether the file is copied or not
As per the task we need to run the image and create a container with name as official as below. And use the volumes concept by copying the sample.txt to container volume
```
docker run --name=official -v /opt/security/:/usr/src -d -it nginx:latest
```
Make sure you login to container and validate the file existing or not
```
docker exec -it container_id /bin/bash
```
ll /usr/src -- to check the file existing or not. File will be existing so that's complete the task.
