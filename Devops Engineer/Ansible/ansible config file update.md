To manage all servers within the stack using Ansible, the Nautilus DevOps team is planning to use a common sudo user among all servers. 
Ansible will be able to use this to perform different tasks on each server. This is not finalized yet, but the team has decided to first perform testing. 
The DevOps team has already installed Ansible on jump host using yum, and they now have the following requirement:

On jump host make appropriate changes so that Ansible can use kirsty as a default ssh user for all hosts. 
Make changes in Ansible's default configuration only —please do not try to create a new config.

Login to jump host as root user by giving sudo su and provide the jump host password

--> cat /etc/ansible/ansible.cfg | grep remote  --- command to find the remote in ansible.cfg

--> from user = root update that to kristy user as per the task

--> vi /etc/ansible/ansible.cfg -- uncomment #rootuser = root to rootuser = kirsty

Task is successfully completed, no need to restart. 


