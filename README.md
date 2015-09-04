# ansible-minecraft
Install Minecraft server on Debian Jessie

Requirements
------------
* [Ansible](http://docs.ansible.com/ansible/intro_installation.html)
* [Vagrant](https://www.vagrantup.com/) If you want to test via Vagrant.
* A Debian Jessie server (May or may not work for Ubuntu).

- You will need to add your server's IP to the `inventories` file

How to run
----------
Example ansible command: `ansible-playbook -i inventories playbook.yml -u <user>`


Acknowledgements
----------------
- Used directions off of a gamepedia Minecraft [Tutorial](http://minecraft.gamepedia.com/Tutorials/Setting_up_a_server)


Things to Consider
------------------
As of right now I am not including any sort of Firewall rules (Such as iptables). Before installing and running any server(particularly minecraft)
you should understand the implications.
