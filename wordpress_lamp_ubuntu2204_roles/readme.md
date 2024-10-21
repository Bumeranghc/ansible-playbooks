# Wordpress on Ubuntu 22.04 LAMP

This playbook uses roles and installs a WordPress website on top of a LAMP environment (**L**inux, **A**pache, **M**ySQL and **P**HP) on an Ubuntu 22.04 machine. A virtualhost will be created with the options specified in the `vars/default.yml` variable file.

## Settings

- `demo_project_php_modules`:  An array containing PHP extensions that should be installed to support your WordPress setup. You don't need to change this variable, but you might want to include new extensions to the list if your specific setup requires it.
- `demo_project_mysql_root_password`: The desired password for the **root** MySQL account.
- `demo_project_mysql_db`: The name of the MySQL database that should be created for WordPress.
- `demo_project_mysql_user`: The name of the MySQL user that should be created for WordPress.
- `demo_project_mysql_password`: The password for the new MySQL user.
- `demo_project_http_host`: Your domain name.
- `demo_project_http_conf`: The name of the configuration file that will be created within Apache.
- `demo_project_http_port`: HTTP port for this virtual host, where `80` is the default. 

## Running this Playbook

Quickstart guide for those already familiar with Ansible:

### 1. Obtain the playbook
```shell
git clone https://github.com/Bumeranghc/ansible-playbooks.git
cd ansible-playbooks/wordpress_lamp_ubuntu2204_roles
```

### 2. Customize Options

```shell
nano vars/default.yml
```

```yml
---
#System Settings
demo_project_php_modules: [ 'php-curl', 'php-gd', 'php-mbstring', 'php-xml', 'php-xmlrpc', 'php-soap', 'php-intl', 'php-zip' ]

#MySQL Settings
demo_project_mysql_root_password: "mysql_root_password"
demo_project_mysql_db: "wordpress"
demo_project_mysql_user: "sammy"
demo_project_mysql_password: "password"

#HTTP Settings
demo_project_http_host: "your_domain"
demo_project_http_conf: "your_domain.conf"
demo_project_http_port: "80"
```

### 3. Run the Playbook

```command
ansible-playbook -l [target] -i [inventory file] -u [remote user] playbook.yml
```
