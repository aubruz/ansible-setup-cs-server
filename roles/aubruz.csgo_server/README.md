aubruz.csgo_server
=========

Download, Install and configure a basic Counter Strike Global Offensive Server

Requirements
------------

Create a steam user. If you want to use another than "steam" you can override the variable `steam_user`.
In order to make the server work you will need to retrieve two tokens:
- csgo_web_api_token can be retrieved [here](https://steamcommunity.com/dev/registerkey). To be able to use workshop maps
- csgo_token can be retrieved [here](https://steamcommunity.com/dev/managegameservers) (Game ID 730). To avoid being stuck with the LAN mode.

Role Variables
--------------

defaults/main.yml:

- steam_user: (default: steam) User that will run the service
- csgo_port: (default: 27015) Port used for the game
- csgo_path: (Default: "/home/{{ steam_user }}/css") Path to the game
- csgo_token: XXXXXXXXXXXXXXXXXXXXXXXXXXX
- csgo_web_api_token: XXXXXXXXXXXXXXXXXXXXXXXXXXX


vars/main.yml:

- csgo_app_id: CS:GO Game ID in Steam
- csgo_config_files: List of config files needed to setup the server


Dependencies
------------

This role is using the role aubruz.steamcmd.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: aubruz.csgo_server, css_port: 27016 }

License
-------

MIT

Author Information
------------------

[aubruz](https://github.com/aubruz)
