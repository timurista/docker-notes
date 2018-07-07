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

