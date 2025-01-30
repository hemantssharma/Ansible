# Ansible Installation and Configuration

## Installation

To install Ansible, run the following commands:
```
sudo apt update
sudo apt install ansible
```
**Install Google Cloud Collection**
To install the Google Cloud collection, run:
```
ansible-galaxy collection install google.cloud
```
**Install Google Authentication**
To install Google authentication, run:
```
sudo apt install pip
sudo pip install google-auth
```
**Default Host File Location**
The default host file is located at:
```
/etc/ansible/hosts
```
## Inventory Configuration
Add the following configuration to your inventory file:

**If you are using ansible for infra configuration:**
```
[local_group]
localhost ansible_connection=local
```
**If you are using ansible for configuration management:**
```
[App]
redhat1 ansible_host=<Pub_IP>
centos1 ansible_host=<Pub_IP>

[App:vars]
ansible_ssh_private_key_file=<key path>

[DB]
ubuntu1 ansible_host=<Pub_IP>
debian1 ansible_host=<Pub_IP>

[DB:vars]
ansible_ssh_private_key_file=<key path>

[all:vars]
ansible_python_interpreter=/usr/bin/python3
ansible_user=<user-name>
```
**List Ansible Inventory Hosts**
To list the Ansible inventory hosts, use the following command:
```
ansible-inventory --list
```
