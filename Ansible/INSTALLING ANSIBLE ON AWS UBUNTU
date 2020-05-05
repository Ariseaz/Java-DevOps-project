# INSTALLING ANSIBLE ON AWS UBUNTU 18.04

## Setup EC2 on AWS

Log in to the EC2 instance with ssh

Swith to root user
```
sudo su -
```

Change hostname to Ansible Master
```
hostname Ansible_Master
```

Install required packages 
```
apt-get update
apt-get install apt-transport-https wget gnupg -y
```

Install Ansible
```
apt-get update
apt-get install ansible
```

Create a local user account named ansible
```
useradd -m -s /bin/bash ansible
```
Give ansible sudo right
```
usermod -aG sudo ansible
```
_Use the SU comand to become the Ansible user_

Generate a SSH key to the Ansible user account
```
su ansible
ssh-keygen
```
Go out from ansible user session
```
exit
```
Add the list of desired Ansible nodes
```
nano /etc/ansible/hosts
```
Sample nodes
```
[nodes]
server1 ansible_host=203.0.113.111
server2 ansible_host=203.0.113.112
server3 ansible_host=203.0.113.113

[all:vars]
ansible_python_interpreter=/usr/bin/python3
```

### SWITCH TO THE NODES (EC2)

On the command-lise of your Ansible node, create a user account named Ansible
```
adduser ansible
```
On the Ansible node, edit the SUDOERS configuration file
```
vi /etc/sudoers
```
Add the following line at the end of the SUDOERS file
```
ansible ALL=(ALL) NOPASSWD:ALL
```

Go back to the Ansible Master server command-line.

Use the ssh-copy-id command to copy the Ansible user account SSH key from the server to the node
```
su ansible
ssh-copy-id 200.100.100.100
```
Now, from the Ansible Master server, try to login on the Ansible node.

You will need to enter the SSH key password
```
su ansible
ssh 200.100.100.100
```
From the Ansible Master server console, test the communication with the Ansible nodes.
```
su ansible
ansible -m ping all
```
## DO SOME CHECK

_On the Ansible Master server console, use the following command to get the Uptime of all Ansible nodes_
```
su ansible
ansible -m raw -a 'uptime' all
```
