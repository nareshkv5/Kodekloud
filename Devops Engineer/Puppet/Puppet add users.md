---

A new teammate has joined the Nautilus application development team, the application development team has asked the DevOps team to create a new user account for the new teammate on application server 2 in Stratos Datacenter. The task needs to be performed using Puppet only. You can find more details below about the task.

Create a Puppet programming file media.pp under /etc/puppetlabs/code/environments/production/manifests directory on master node i.e Jump Server, and using Puppet user resource add a user on all app servers as mentioned below:

Create a user john and set its UID to 1752 on Puppet agent nodes 2 i.e App Servers 2.
Notes: :- Please make sure to run the puppet agent test using sudo on agent nodes, otherwise you can face certificate issues. In that case you will have to clean the certificates first and then you will be able to run the puppet agent test.

:- Before clicking on the Check button please make sure to verify puppet server and puppet agent services are up and running on the respective servers, also please make sure to run puppet agent test to apply/test the changes manually first.

:- Please note that once lab is loaded, the puppet server service should start automatically on puppet master server, however it can take upto 2-3 minutes to start.

- Login to the below directory from thor as root user and change directory (cd /etc/puppetlabs/code/environments/production/manifests) folder and create media.pp file

- And copy the below code to media.pp file


```
 class user_creator {
user { 'john':
ensure   => present,
uid => 1752,
 }
}
node 'stapp01.stratos.xfusioncorp.com', 'stapp02.stratos.xfusioncorp.com', 'stapp03.stratos.xfusioncorp.com' {
  include user_creator
}
```

- Then run the below command to test and validate the media.pp puppet file

 ` puppet parser validate media.pp `

- The login to each 3 three servers (stapp01/stapp02/stapp03) and run the agent to check whether user is created or not.
- First check the user existed or not with cat /etc/passwd | grep 'john'
- Then run the below command in each server to get the user created. That's it your taks is finished.

` puppet agent -tv `
