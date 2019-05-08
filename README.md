# ssh-access
### Introduction:
Grant/Revoke SSH access to a user on a single or group of instances.

### Use below command if the ansible is not setup on the base machine
RUN:
```bash
$ chmod +x ansible.sh
$ ./ansible.sh
```
### Usage:

add new user and grant SSH access:
```bash
$ansible-playbook -i inventory/ -e "action=grant" playbooks/ssh.yml
```

grant SSH access to an existing user:
```bash
$ansible-playbook -i inventory/ -e "action=grant" playbooks/ssh.yml --skip-tags=add
```

revoke SSH access from a user:
```bash
$ansible-playbook -i inventory/ -e "action=revoke" playbooks/ssh.yml --skip-tags=remove
```

remove user, hence revoke SSH access as well:
```bash
$ansible-playbook -i inventory/ -e "action=revoke" playbooks/ssh.yml
```

## Notes
 - Under [instances] group in inventory/hosts files please add IPs or DNS of target instances.
 - Update the varibale "user_name" as per requirements.
 - Please create a directory under "sshkeys" directory of same name as user name and put its SSH pub key under it.
 - I have tested this on AWS instances as target instances so I have used ubuntu. Please update the user in "ssh.yml" who has access to target servers and the machine from where you will run Ansible.
