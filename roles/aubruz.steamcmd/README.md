aubruz.steamcmd
=========

Download and install steamcmd

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

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

https://github.com/aubruz
