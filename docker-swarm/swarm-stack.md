# Swarm Stacks and Production Grade Compose

Stacks are composed files of production for swarm

Docker 1.14 added stacks
  they accept compose files as delcarative
  for services, networks, volumes

Docker stack deploy
stack manages all of this
  external
easier
new "deploy" ie replicas, failovers, etc. not build command yet. Build CI does it, then in repo, this stacj pulls them down

docker will ignore deploy info

docker-compose is best for local develop on machine

`docker stack deploy -c stack-examples/voteapp.yml`
- c is for compose option above

`docker stack ls`
to list out stacks

this app will run the voting at 5000, the results at 5001, and the list of running nodes and replicas on port 8080
