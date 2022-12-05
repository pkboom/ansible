# Installation

```sh
sudo apt-add-repository -y ppa:ansible/ansible
sudo apt update
sudo apt install -y ansible
```

# Define servers

```
# /etc/ansible/hosts
[web]
192.168.22.10
192.168.22.11
```

# Commands

```sh
ansible all -m ping
ansible all -m ping -s -k -u vagrant
# all - Use all defined servers from the inventory file
# -m ping - Use the “ping” module, which simply runs the ping command and returns the results
# -s - Use “sudo” to run the commands
# -k - Ask for a password rather than use key-based authentication
# -u vagrant - Log into servers using user vagrant
```

```sh
ansible all -s -m apt -a 'pkg=nginx state=installed update_cache=true'
ansible web -s -m apt -a 'pkg=nginx state=installed update_cache=true'
# all - Run on all defined hosts from the inventory file
# web - Run on servers under the label 'web'
# -s - Run using sudo
# -m apt - Use the apt module
# -a 'pkg=nginx state=installed update_cache=true' - Provide the arguments for the apt
```

```sh
ansible-playbook nginx.yml
ansible-playbook -s -k -u vagrant nginx.yml
```
