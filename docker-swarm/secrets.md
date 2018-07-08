## Easiest Secure Solution

out of box support in swarm

### What is a secret?
  - username, passwords
  - tls certs, keys
  - ssh keys
  - any data you would prefer NOT on front page of news

string or binary up to .5MB in size
`swarm raft db`
tls between managers and workers
  - use that existing channel
  - put them into swarm db then assign to services, ie stack file
  - to tell swarm who is allowed to use it
  - docker worker keeps it secure in memory online

looks like file, but in memory only. RAM fs file
`/run/secrets/<secret_name>`
`/run/secrets/<secret_alias>`

### secrets
`docker secret create psql_user psql_user.txt`
spits back ID: y7lb4klih9tzenh5bazy8j1ae
-- first stores it on host, bash history for root user

`echo "myDBpassWORD" | docker secret create psql_pass -`
read from standard input

```sh
docker service create --name psql --secret psql_user --secret psql_pass -e POSTGRES_PASSWORD_FILE=/run/secrets/psql_pass -e POSTGRES_USER_FILE=/run/secrets/psql_user postgres
```
You can inspect the secrets fils inside run to see that we have saved those into the running service.


### secrets sample 2
`docker service create --name search --replicas 3 -p 9200:9200 elasticsearch:2`

-- to create service for searching

`docker stack deploy -c docker-compose.yml mydb`

in secrets2 to deploy that compose file

`docker stack rm mydb` <-- removes

note that you DONT want to copy over the files or you want to remove them from the copy command so you are not saving secrets to your image
