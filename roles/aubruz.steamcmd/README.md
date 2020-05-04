aubruz.steamcmd
=========

Download and install steamcmd

Requirements
------------

Have a "steam" user. If you don't, you can override the variable `steam_user`.

Role Variables
--------------

defaults:
steam_user: (default: steam) User that will be used to download and install SteamCMD
steamcmd_path: (default: "/home/{{ steam_user }}/steamcmd") Path where SteamCMD will be installed

vars:
steamcmd_packages: Packages that are needed for SteamCMD in order to work


Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: aubruz.steamcmd, steam_user: john }

License
-------

MIT

Author Information
------------------

[aubruz](https://github.com/aubruz)
