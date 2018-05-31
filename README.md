# swarm-with-ansible
Introduce how to build swarm cluster with ansible

Step1:

build your own mirror

Step2:

build your own registry

Step3:

if your machine have bond1 interface then you can use this yml

Step4:

copy your config.json to /root/.docker/

config.json include your docker registry auth information

Step5:

ansible -i env/hosts swarm.yml

Step6:

eg:

cat docker-compose.yml

version: '3.2'
services:
  service_name:
    image: registry_url/image_name:0.0.1
    networks:
      - bridge

networks:
  bridge:
    external: true
    
docker-compose -f docker-compose.yml config > docker-stack.yml

docker stack deploy -c docker-stack.yml --with-registry-auth stack_name
