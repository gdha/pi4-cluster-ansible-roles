# cluster-ansible-playbooks
Ansible playbooks for common provisioning tasks on Raspberry Pi 4 cluster

## Requirements
1. Python 3
1. Ansible

## Using a vault for the OpenSSH public key
```bash
$ cat >>.gitignore <<EOF
.my_password
EOF

$ echo "your secret password!" > .my_password

$ ansible-vault encrypt --vault-password-file .my_password ~/.ssh/id_rsa.pub --output user/files/id_rsa.pub.encrypted
Encryption successful

$ ansible-vault view --vault-password-file .my_password user/files/id_rsa.pub.encrypted
ssh-rsa A....
```

## Usage
```bash
$ ansible-playbook provision.yml -k --vault-password-file .my_password
```

### Reference

- Original GIT project https://github.com/ikaruswill/cluster-ansible-roles.git
