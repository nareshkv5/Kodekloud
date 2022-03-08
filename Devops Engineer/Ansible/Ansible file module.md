---
The Nautilus DevOps team is working to test several Ansible modules on servers in Stratos DC. Recently they wanted to test the file creation on remote hosts using Ansible. 
Find below more details about the task:

a. Create an inventory file ~/playbook/inventory on jump host and add all app servers in it.

b. Create a playbook ~/playbook/playbook.yml to create a blank file /home/opt.txt on all app servers.

c. The /home/opt.txt file permission must be 0777.

d. The user/group owner of file /home/opt.txt must be tony on app server 1, steve on app server 2 and banner on app server 3.

Note: Validation will try to run the playbook using command ansible-playbook -i inventory playbook.yml, so please make sure the playbook works this way without passing any extra arguments.

----

As per the instruction move to playbook folder and create inventory file

vi inventory
```
stapp01 ansible_host=172.16.238.10 ansible_ssh_pass=Ir0nM@n  ansible_user=tony
stapp02 ansible_host=172.16.238.11 ansible_ssh_pass=Am3ric@  ansible_user=steve
stapp03 ansible_host=172.16.238.12 ansible_ssh_pass=BigGr33n  ansible_user=banner
```
cat inventory to view the file details

ansible all -a "ls -lsd /home/web.txt" -i inventory  -- command to view to check inventory file working or not

since there is no file and directory we won't get the output

Create a playbook with the below ansible code vi playbook.yml
```
- name: create file in appservers
  hosts: stapp01, stapp02, stapp03
  become: yes
  tasks:
    - name: create file and set properties
      file:
        path: /home/opt.txt
        owner: "{{ ansible_user }}"
        group: "{{ ansible_user }}"
        mode: "0755"
        state: touch
```
ansible-playbook -i inventory playbook.yml -- execute the command to execute the tasks mentioned in playbook by using inventory file
The task will be successful and it will shows the files creates in the specfic servers

Run the below command again to view the details in the 

ansible all -a "ls -lsd /home/web.txt" -i inventory -- It gonna show the files existed or not. And your task is success
