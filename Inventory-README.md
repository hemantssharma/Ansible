**# Ansible Installation:**
```
sudo apt update
sudo apt install ansible
```
host File location: 
```
/etc/ansible/hosts
```
##################################################################################
##################################################################################
[local_group]
localhost ansible_connection=local
##################################################################################
##################################################################################
ansible-inventory --list
**********************************************************************************
ansible-galaxy collection install google.cloud
**********************************************************************************
sudo apt install pip
sudo pip install google-auth
**********************************************************************************

##################################################################################
##################################################################################

[App]
redhat1 ansible_host=34.45.45.37
centos1 ansible_host=35.238.132.212

[App:vars]
ansible_ssh_private_key_file=/home/hemant_sharma/keys/redhat-key

[DB]
ubuntu1 ansible_host=35.193.83.0
debian1 ansible_host=104.197.66.80

[DB:vars]
ansible_ssh_private_key_file=/home/hemant_sharma/keys/ubuntu-key

[all:vars]
ansible_python_interpreter=/usr/bin/python3
ansible_user=dell

##################################################################################
##################################################################################
