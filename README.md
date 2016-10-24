### A Ubuntu Virtual Machine to manage Workspace on Windows & Running Ansible

## Getting Started
---
1. Download and Install [VirtualBox](https://www.virtualbox.org/)
2. Download and Install [Vagrant](https://www.vagrantup.com/)
3. Download and Install [GitBash](https://git-scm.com/downloads)
4. Checkout Source code & Run Vagrant Up
```
#open gitbash
cd yourworkspace
git git@github.com:giappv/vagrant_ansible.git
cd vagrant_ansible
vagrant plugin install vagrant-hostmanager
vagrant up
```

### Checking Ansible is working
```
vagrant ssh #login to VM
ansible --version #check if ansible installed
```

It gave me this output, means ansible is working
```
ansible 2.1.2.0
  config file = /etc/ansible/ansible.cfg
  configured module search path = Default w/o overrides
```

```
cd /vagrant #this folder will be mounted to yourworkspace folder, 
ls -la #output will be similar as the below
drwxrwxrwx  1 vagrant vagrant    0 Oct 24 10:15 site1.com
drwxrwxrwx  1 vagrant vagrant    0 Oct 24 10:16 site2.com
drwxrwxrwx  1 vagrant vagrant    0 Oct 24 10:16 site3.com
drwxrwxrwx  1 vagrant vagrant    0 Oct 24 10:16 site4.com
drwxrwxrwx  1 vagrant vagrant    0 Oct 24 10:17 site5.com
drwxrwxrwx  1 vagrant vagrant 4096 Oct 24 11:00 vagrant_ansible
```

Now we can walk to any specific project easily and run ansible there, for example:
```
cd site1.com/devops/ansible
ansible-playbook -i inventories/staging playbook.yml
```