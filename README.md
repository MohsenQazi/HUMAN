Set some variable for Domain, Let's Encrypt, Traefik dashboard, IP Whitelistening:
`export DOMAIN=.... MAIL=.... TraefikPass=$(openssl passwd whoami) WhiteList="A, B, C"`
`WorkerIP=$(docker node inspect -f '{{ .Status.Addr }}' worker)`

Initialize a swarm cluster:
`docker swarm init`

To deploy the stack:
`docker stack deploy -c accounting.yml accounting`
