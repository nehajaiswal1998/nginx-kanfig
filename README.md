# Ansible Role: 
Nginx

Installs Nginx on RedHat/CentOS, Debian/Ubuntu

This role installs and configures the latest version of Nginx from the Nginx yum repository on RedHat-based systems and  apt on Debian-based systems. 

## Resources Used

Used Ansible Master server as Ubuntu and Client server on Redhat
Ansible Master server is installed with Ansible2.

## Role Variables

In vars folder variable file for Debian is Debian.yml and for RedHat there is RedHat.yml
 
 In 'vars/Debian.yml' there are following variables
 # Variables for Debian system
    root_group: root
    nginx_conf_path: /etc/nginx/conf.d
    nginx_conf_file_path: /etc/nginx/nginx.conf
    nginx_mime_file_path: /etc/nginx/mime.types
    nginx_pidfile: /run/nginx.pid
    nginx_vhost_path: /etc/nginx/sites-enabled
    nginx_default_vhost_path: /etc/nginx/sites-enabled/default
    __nginx_user: "www-data"

 In 'vars/RedHat.yml' there are following variables
 # Variables for RedHat system
    root_group: root
    nginx_conf_path: /etc/nginx/conf.d
    nginx_conf_file_path: /etc/nginx/nginx.conf
    nginx_mime_file_path: /etc/nginx/mime.types
    nginx_pidfile: /var/run/nginx.pid
    nginx_vhost_path: /etc/nginx/conf.d
    nginx_default_vhost_path: /etc/nginx/conf.d/default.conf
    __nginx_user: "nginx"

## Role Hirarachy

roles/defaults = It includes main.yml file which contains variables for Ubuntu and Redhat

roles/handlers = It includes main.yml file which contains code for restart services

roles/tasks = It includes main.yml and following files for targeting to other files as per OS family
 Debian.yml  RedHat.yml  main.yml

roles/templates = It includes following configuration files for nginx
 nginx.conf.j2 nginx.repo.j2

roles/vars = it includes foloowing variable files for RedHat and Debian
 Debian.yml RedHat.yml

inventory/hosts :It includes hosts file

## Example Playbook

    - hosts: nginx
      roles:
        - { role: roles }



