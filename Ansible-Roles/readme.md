# Running the Role

## Set role path

We can add this file path to the /etc/ansible/ansible.cfg file:

```
roles_path=path/to/roles

# Assuming our nginx Role is located at /.ansible/roles/nginx, we’ll be all set to run this
roles_path=~/.ansible/roles
```

## Run Playbook

```sh
# if sudo: "yes" is set, you can omit -s
ansible-playbook -s -k -u vagrant server.yml
```

# Ansible Facts

Ansible facts all start with `anisble_` and are globally available for use any place variables can be used: Variable files, Tasks, and Templates.

# Ansible Vault

Vault allows you to encrypt any Yaml file, which typically boil down to our Variable files. Vault will
not encrypt Files and Templates.

```sh
# create a new Variable file:
ansible-vault create vars/main.yml
Vault Password:

# To run this Playbook, we need to tell Ansible to ask for the Vault password,
# as we’re running a Role which contains an encrypted file:
ansible-playbook --ask-vault-pass provision.yml
```
