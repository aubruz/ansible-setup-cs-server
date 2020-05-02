aubruz.css_server
=========

Download, Install and configure a basic Counter Strike Source Server

Requirements
------------

Create a steam user. If you want to use another than "steam" you can override the variable `steam_user`

Role Variables
--------------

defaults/main.yml

steam_user: (default: steam) User that will run the service
css_port: (default: 27015) Port used for the game
css_path: (Default: "/home/{{ steam_user }}/css") Path to the game

vars/main.yml:

css_app_id: Counter Strike Source Game ID in Steam
css_config_files: List of config files needed to setup the server


Dependencies
------------

This role is using the role aubruz.steamcmd.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: aubruz.css_server, css_port: 27016 }

License
-------

MIT

Author Information
------------------

[aubruz](https://github.com/aubruz)
