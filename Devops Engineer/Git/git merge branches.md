Git merge branches

The Nautilus application development team has been working on a project repository /opt/news.git. This repo is cloned at /usr/src/kodekloudrepos on storage server in Stratos DC. 
They recently shared the following requirements with DevOps team:

a. Create a new branch datacenter in /usr/src/kodekloudrepos/news repo from master and copy the /tmp/index.html file (on storage server itself). 
Add/commit this file in the new branch and merge back that branch to the master branch. Finally, push the changes to origin for both of the branches.

```
git status by going under /usr/src/kodekloudrepos/news 

git checkout -b datacenter

git status

git branch -- to view the branches

cp /tmp/index.html /usr/src/kodekloudrepos/news/

ll /usr/src/kodekloudrepos/news/ -- to check the files added 

git add index.html  -- to add the file to the branch
 
git commit -m "add news"

git checkout master

git merge datacenter -- merging branch datacenter

git push -u origin datacenter -- push the code to datacenter

git push -u origin master -- push code to master branch
```


