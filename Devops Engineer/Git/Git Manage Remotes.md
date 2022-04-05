---
The xFusionCorp development team added updates to the project that is maintained under /opt/apps.git repo and cloned under /usr/src/kodekloudrepos/apps. 
Recently some changes were made on Git server that is hosted on Storage server in Stratos DC. The DevOps team added some new Git remotes, so we need to update remote on /usr/src/kodekloudrepos/apps repository as per details mentioned below:

a. In /usr/src/kodekloudrepos/apps repo add a new remote dev_apps and point it to /opt/xfusioncorp_apps.git repository.

b. There is a file /tmp/index.html on same server; copy this file to the repo and add/commit to master branch.

c. Finally push master branch to this new remote origin.
---

First Login to natasha server by doing 

ssh natasha@ststor01 then sudo su - to move to root user

cd /usr/src/kodekloudrepos/apps-- move to the above folder 

check which branch we are in by using 
git branch -a 

As per task add remote repo and poing to given directory as below

git remote add dev_apps /opt/xfusioncorp_apps.git/

Now copy index.html to same server 

cp /tmp/index.html . -- post copy initialize the repository

git init

git status

git add index.html

git status

git commit -m "add index.html"

git push -u dev_apps master

Now to check git status & git branch -a
