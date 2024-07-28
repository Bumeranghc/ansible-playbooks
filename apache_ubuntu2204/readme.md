# Apache on Ubuntu 22.04

This playbook will install the Apache 2 web server on an Ubuntu 22.04 machine. A virtualhost will be created with the options specified in the `vars/default.yml` variable file.

## Settings

- `app_user`: a remote non-root user on the Ansible host that will own the application files.
- `http_host`: your domain name.
- `http_conf`: the name of the configuration file that will be created within Apache.
- `http_port`: HTTP port, default is 80.
- `disable_default`: whether or not to disable the default Apache website. When set to true, your new virtualhost should be used as default website. Default is true.


## Running this Playbook

Quick Steps:

### 1. Obtain the playbook
```shell
git clone https://github.com/Bumeranghc/ansible-playbooks.git
cd ansible-playbooks/apache_ubuntu2204
```

### 2. Customize Options

```shell
nano vars/default.yml
```

```yml
#vars/default.yml
---
app_user: "sammy"
http_host: "your_domain"
http_conf: "your_domain.conf"
http_port: "80"
disable_default: true
```

### 3. Run the Playbook

```command
ansible-playbook -l [target] -i [inventory file] -u [remote user] playbook.yml
```