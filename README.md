# Installation for OpenLDAP

## Clone 
```
git clone git@github.com:harupu/ansible-ldap-ubuntu18.4.git
```

## Install packages
python is required by ansible.
```
ssh -t [remote-user]@[hostname] sudo apt install -y python
```

## Config
Change your admin/testuser password first.
```
vi ./ansible-ldap-ubuntu18.4/roles/ldap/vars/main.yml
```

Target host
```
vi ./ansible-ldap-ubuntu18.4/inventories/develop/hosts
```

## Execute
```
cd ansible-ldap-ubuntu18.4
ansible-playbook -u [remote_user] ldapservers.yml
```

When remote server allows password login for development use, please use '-K -k' options.

Default env variable is in ansible.cfg. If you want to change environment, use "-i" option to override default.

This playbook creates default user named 'testuser'. You can check account info by this command:
```
ldapsearch -x cn=testuser -b dc=example,dc=local
```