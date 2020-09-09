# Pi4-cluster-ansible-playbooks
Ansible playbooks for common provisioning tasks on Raspberry Pi 4 cluster. We want to provision with our own account

## Requirements
1. Ubuntu 20.04 LTS Raspberry Pi 64-bit version 
2. Python 3
3. Ansible
4. Default user is 'ubuntu'
5. Define your account in files inventory.yml and user/defaults/main.yml

## Using a vault for the OpenSSH public key
```bash
$ cat >>.gitignore <<EOF
.my_password
EOF

$ echo "your secret password!" > .my_password

$ ansible-vault encrypt --vault-password-file .my_password ~/.ssh/id_rsa.pub --output user/files/id_rsa.pub.encrypted
Encryption successful

$ ansible-vault view --vault-password-file .my_password user/files/id_rsa.pub.encrypted
ssh-rsa AAAAA....
```

## Usage
```bash
$ ansible-playbook provision.yml -k --vault-password-file .my_password
```

### Reference

- Original GIT project https://github.com/ikaruswill/cluster-ansible-roles.git
