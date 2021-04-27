## Ansible Notes

Ansible uses python, if a server does not have python make sure to install


inventory files are similar to ini format (not exactly)


Docker to create local hosts

To create a linux machine running ssh

` docker run -d -P --name test_sshd rastasheep/ubuntu-sshd`

`sudo docker port test_sshd 22`

To get the IP Address

`sudo docker inspect -f "{{ .NetworkSettings.IPAddress }}" test_sshd`

172.17.0.2

`ssh root@172.17.0.2`

password is `root`

To pass user password 

in inventory or config file use ansible_password= < password > or use --ask-pass parameter

`sudo apt install sshpass`

Passing Adhoc commands

`ansible test_ssh -a "free -h" -u root --ask-pass`

Running a playbook

`ansible-playbook <playbook.yaml>`

limiting where playbooks or ansible commands run 

`ansible-playbook <playbook.yaml> --limit db`

    only runs the playbook on db

View list of inventory

`ansible-inventory -i <inventory-file> --list`


*how to add known hosts ??*

in ansible config file:

    [defaults]
    host_key_checking = False

source :
[How to ignore ansible SSH authenticity checking?](https://stackoverflow.com/questions/32297456/how-to-ignore-ansible-ssh-authenticity-checking)


