# Docker. Run docker as systemd service

Install and run the Docker server with Linux containers.
Manage containers as are hosts via dynamic-inventory.

## Variables
Variables defines in `./vars/default_vars.yml`

     num_containers: 4
     container_name: docker
     container_image: nginx
     ....
     and etc.

## Deploy Docker server

Start deployment Docker server:

     $ ansible-playbook deploy_containers.yml

This playbook:

- install Docker-CE as systemd service
- configuring remote access to Docker API ( settings in `./files/override.conf` )
- create default docker containers ( amount in var `num_containers: 4`)

## Managing Docker containers as hosts

Start `manage_containers.yml` wich contains 2 plays:

     $ ansible-playbook manage_containers.yml

1. create In-memory inventory (remote Docker API connection)
2. execute Play which works with docker containers as hosts ( i.e., copy a web page to Nginx server )