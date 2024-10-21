# Ansible Role: phpMyAdmin

![](https://i.imgur.com/waxVImv.png)
### [View all Roadmaps](https://github.com/nholuongut/all-roadmaps) &nbsp;&middot;&nbsp; [Best Practices](https://github.com/nholuongut/all-roadmaps/blob/main/public/best-practices/) &nbsp;&middot;&nbsp; [Questions](https://www.linkedin.com/in/nholuong/)
<br/>

Installs phpMyAdmin on RHEL/CentOS/Debian/Ubuntu.

phpMyAdmin is a simple interface for interacting with MySQL databases via a web browser. It is not necessarily the most secure or efficient method of managing databases, but for those who need a GUI, this one is better than many others. I (nholuong) would personally never run it on a production server, nor do I use it myself (I use Sequel Pro or simply interact with the database via CLI/APIs), but it seems many people like it (especially people stuck on a Windows machine with no good MySQL GUIs :).

## Requirements

**RedHat/CentOS**: Requires the EPEL repository on RedHat/CentOS 6.x hosts. You can install the EPEL repository using the `nholuong.repo-epel` role.

**Debian/Ubuntu**: None.

## Role Variables

    phpmyadmin_enablerepo: "epel"

(RedHat/CentOS only) If you have enabled any additional repositories (might I suggest [nholuong.repo-epel](https://github.com/nholuong/ansible-role-repo-epel) or [nholuong.repo-remi](https://github.com/nholuong/ansible-role-repo-remi)), those repositories can be listed under this variable (e.g. `remi,remi-php73`). This can be handy, as an example, if you want to install the latest version of PHP 7.3 with the latest version of phpMyAdmin, which is in the Remi repository.

    phpmyadmin_config_file: /etc/phpmyadmin/config.inc.php

The path to the phpMyAdmin config file.

Available variables are listed below, along with default values (see `defaults/main.yml`):

    phpmyadmin_mysql_host: localhost
    phpmyadmin_mysql_port: ""
    phpmyadmin_mysql_socket: ""
    phpmyadmin_mysql_connect_type: tcp

These variables define the connection method and hostname phpMyAdmin will use to connect to the MySQL server.

    phpmyadmin_mysql_user: root
    phpmyadmin_mysql_password: "{{ mysql_root_password }}"

The username and password with which phpMyAdmin will attempt to log into the MySQL server. The `mysql_root_password` should be set as part of the `nholuong.mysql` role, but you can change the user and password to another account entirely, and you most defintely *should*, especially if you're connecting to a non-development database server!

## Dependencies

  - nholuong.apache
  - nholuong.mysql
  - nholuong.php
  - nholuong.php-mysql

## Example Playbook

    - hosts: utility
      vars_files:
        - vars/main.yml
      roles:
        - { role: nholuong.phpmyadmin }

*Inside `vars/main.yml`*:

    phpmyadmin_mysql_user: special_user
    phpmyadmin_mysql_password: secure_password_here

## TODO

  - Make default configuration more flexible (not everyone wants phpmyadmin to autologin as root).

# 🚀 I'm are always open to your feedback.  Please contact as bellow information:
### [Contact ]
* [Name: nho Luong]
* [Skype](luongutnho_skype)
* [Github](https://github.com/nholuongut/)
* [Linkedin](https://www.linkedin.com/in/nholuong/)
* [Email Address](luongutnho@hotmail.com)

![](https://i.imgur.com/waxVImv.png)
![](Donate.png)
[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/nholuong)

# License
* Nho Luong (c). All Rights Reserved.🌟
