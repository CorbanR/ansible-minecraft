# docker-builder
Build a Minecraft Docker container using Packer, and Ansible.
This was used to build [corbanr/minecraft:1.8.8](https://hub.docker.com/r/corbanr/minecraft/)

Requirements
------------
* [Ansible](http://docs.ansible.com/ansible/intro_installation.html).
* [Vagrant](https://www.vagrantup.com/)
  * [VirtualBox](https://www.virtualbox.org/wiki/Downloads) or [vmware](http://www.vmware.com/).
* [Docker Hub](https://hub.docker.com/) account.


Required Variables
------------------
Please update the following variables located in  `ansible-minecraft/docker-builder/vagrant.yml`
```
    docker_email: "<email>" #Docker Hub email
    docker_username: "<username>" #Docker Hub username
    docker_password: "<password>" #Docker Hub password
    docker_repository: "<repository>" #Docker hub repository and optional tag. Example "corbanr/minecraft:1.8.8"

```

Optional Variables
------------------
Optional Variables `ansible-minecraft/docker-builder/packer.yml`

```
    minecraft_version: 1.8.8
    minecraft_url: "https://s3.amazonaws.com/Minecraft.Download/versions/{{ minecraft_version }}/minecraft_server.{{ minecraft_version }}.jar"
    minecraft_sha256sum: "39aef720dc5309476f56f2e96a516f3dd3041bbbf442cbfd47d63acbd06af31e"
    java_options: "-Xms2048M -Xmx2048M -jar {{ install_location }}/minecraft_server.{{ minecraft_version }}.jar nogui"

```

Building
--------
Once you have updated the required variables (and or optional ones) run
`vagrant up` this will build and push a Minecraft Docker container to the Docker Hub repository you have chosen.

Troubleshooting
---------------
To view progress or to troubleshoot run `vagrant ssh`. Logs are located `/tmp/packer.log`, `/tmp/meta-data.log`, and `/tmp/push.log`
