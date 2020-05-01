# Ansible setup CS server

Creating and configuring a dedicated server can be a daunting task. Sometimes you just want to play without thinking about the system behind the server.
That is why I made a couple scripts to configure and launch a Counter Srike dedicated server with [Ansible](https://www.ansible.com/) for Source (CSS) and Global Offensive (CS:GO).

## Why Ansible?

Ansible is an open-source software provisioning, configuration management, and application-deployment tool that runs on Mac, Windows and Linux. It can configure softwares and deploy them on many servers at once with a single little script.

Here is the [link](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) to install Ansible.


## Architecture

There is five [playbooks](https://docs.ansible.com/ansible/latest/user_guide/playbooks.html) in this project:
  - setup_users.yml
  - setup_system.yml
  - setup_css.yml
  - setup_csgo.yml
  - setup_from_scratch.yml

Because my servers had [CentOS](https://www.centos.org/) installed, the scripts should work easily on CentOS / RedHat / Fedora. A few ajustements need to be made in order to make it work on Ubuntu/Debian.

The group cs_servers is used to reference your server(s). You can replace my-server-name.com with your server name or ip in the [inventory](#) file.

All the variables are found in [group_vars/cs_servers.yml](#). Please read it before launching any script. A few variables need to be set in order to adapt to your setup.

### setup_users.yml

This script will make sure that the designated users in group_vars/cs_server.yml are created and that their keys are setup to connect without password. In this project there are two users, a superuser called centos and a steam user that will run the services (No keys or password will be set for this user).

### setup_system.yml

This script installs and configures the firewall firewalld, open the needed ports for the game, restricts ssh access with a key and forbid root ssh connections. This script is optional and was created only to follow server security best practices.

### setup_css.yml

This script installs [SteamCMD](https://developer.valvesoftware.com/wiki/SteamCMD) if not already and use it to download Counter Strike Source. It then creates a systemd service that will launch the server.

**Warning:** The download speed can be really slow sometimes. The script will download about 2G. It can take a couple hours to finish.

### setup_csgo.yml

This script installs [SteamCMD](https://developer.valvesoftware.com/wiki/SteamCMD) if not already and use it to download Counter Strike Global Offensive. It then creates a systemd service that will launch the server.

**Warning:** The download speed can be really slow sometimes. The script will download about 24G (Last time I checked). It can take a couple hours to finish. (Took me a night...)

### setup_from_scratch.yml

This script executes all the scripts above in the same order if you want to install CSS and CS:GO.

## Launch scripts

Once you modified ansible.cfg, group_vars/cs_servers.yml and inventory you can execute the playbooks you want like this: `ansible-playbook playbook.yml`

e.g. `ansible-playbook setup_users.yml`
