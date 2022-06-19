The Nautilus development team shared requirements with the DevOps team regarding new application development.—specifically, they want to set up a Git repository for that project. Create a Git repository on Storage server in Stratos DC as per details given below:

Install git package using yum on Storage server.

After that create a bare repository /opt/apps.git (make sure to use exact name). Please follow the below set of commands to finish the respective task.
- Use the below set of commands to install git and create a bare repository with the given folder.

```
yum install git -y
rpm -qa | grep git
git init --bare /opt/apps.git
ll /opt
cd /opt
git status
```
