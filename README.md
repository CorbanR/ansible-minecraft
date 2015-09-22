# ansible-minecraft
Install Minecraft on Debian Jessie.

- To build a Minecraft Docker container see `docker-builder/README.md`.
- To deploy a Minecraft Docker container see `docker-deploy/README.md`.

To install Minecraft without Docker, continue :).

Requirements
------------
* [Ansible](http://docs.ansible.com/ansible/intro_installation.html).
* [Vagrant](https://www.vagrantup.com/) (If you want to build the Docker container).
  * [VirtualBox](https://www.virtualbox.org/wiki/Downloads) or [vmware](http://www.vmware.com/).
* A Debian Jessie server (May work on Ubuntu).

- You will need to add your server's IP to the `inventories` file.

How to run
----------
Example ansible command: `ansible-playbook -i inventories playbook.yml -u <user>`.

Configurable options
--------------------
To see all available configurable options and their defaults see `roles/minecraft/defaults/main.yml`.

Example Playbook:

```

- hosts: minecraft
  become: yes
  vars:
    update_server: yes
    agree_to_eula: "true" #Do you agree to the eula? See https://account.mojang.com/documents/minecraft_eula
    install_location: "/home/minecraft"
    minecraft_version: 1.8.8
    minecraft_url: "https://s3.amazonaws.com/Minecraft.Download/versions/{{ minecraft_version }}/minecraft_server.{{ minecraft_version }}.jar"
    minecraft_sha256sum: "39aef720dc5309476f56f2e96a516f3dd3041bbbf442cbfd47d63acbd06af31e"
    java_options: "-Xms2048M -Xmx2048M -jar {{ install_location }}/minecraft_server.{{ minecraft_version }}.jar nogui" #Change the Xms and Xmx values base on the resources of your server.
    white_list: "true"
    white_list_include:
      - username1
      - username2
  roles:
    - minecraft

```

Acknowledgements
----------------
- Used directions off of a gamepedia Minecraft [Tutorial](http://minecraft.gamepedia.com/Tutorials/Setting_up_a_server)


Things to Consider
------------------
As of right now I am not including any sort of Firewall rules (Such as iptables). Before installing and running any server(particularly minecraft)
you should understand the implications.
