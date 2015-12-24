docker-deploy
-------------
Deploy a Minecraft Docker container.

Requirements
------------
* A Debian Jessie server (May work on Ubuntu)
* Update `inventory` with your server's IP

Optional Variables
------------------
* View/Modify `playbook.yml`
```
    - name: Deploy Minecraft Docker container
      docker:
        name: minecraft
        image: corbanr/minecraft:1.8.9
        state: reloaded
        pull: missing
        restart_policy: always
        restart_policy_retry: 10
        ports:
        - "25565:25565"
        env:
            JAVA_XMS: "512m"
            JAVA_XMX: "512m"
```
How to run
----------
`ansible-playbook -i inventories playbook.yml -u <user>`
