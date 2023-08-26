About
-----

Ansible role for ___ install. This role is build & tested on fedora/ubuntu (centos/debian).
Some dependencies are involved like other ansible role.

# Installation of ansible

## Ubuntu
```bash
git clone <insert_repo_url>
sudo apt install python3-pip

cd <insert_role_name>
python3 -m venv .
source bin/activate
pip install --upgrade pip
pip install requierement.txt

```

## Fedora
````bash
git clone <insert_repo_url>
sudo yum install python3-pip

cd <insert_role_name>
python3 -m venv .
source bin/activate
pip install --upgrade pip
pip install requierement.txt
````

# Create host file

The host file is going to tell ansible what server should be deployed. Please refer to [ansible documentation](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html) to have a better understanding

## localhost

If you plan to deploy from your current host, then use the hosts file provided

## remote_host
````bash
cat << EOF > hosts
[<insert_product_name>]
host1 ansible_ssh_host=192.168.1.4 OR dns
EOF

````

## multiple machine
````bash
cat << EOF > hosts
[<insert_product_name>]
host1 ansible_ssh_host=192.168.1.4
host2 ansible_ssh_host=my-awesome-node.com
host3 ansible_ssh_host=localhost

EOF

````

Variables
---------
Those variable may need some adjustement depending on your os

```yml

```

Usage
-----

```yml
roles:
  - <insert_role_name>
```

Run
-------

    Replace USER with the remote or local one desired.
    -k & -K ask for password first one for ssh connexion, second one foor privilege escalation. Your user need to be able to use sudo.

    if not, then run

## Ubuntu
```bash
usermod -aG sudo your_user

```

## Fedora
````bash
usermod -aG wheel your_user

````

```bash
  ansible-galaxy install -r requirements.yml
  ANSIBLE_USER = your_user
  ansible-playbook playbook.yml -i hosts -k -K -u ${ANSIBLE_USER} -v -c paramiko -D
```
