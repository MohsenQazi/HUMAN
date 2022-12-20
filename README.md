First of all, go to two directories and build the images:
```
docker build -t 127.0.0.1:5000/manage_app .
docker build -t 127.0.0.1:5000/auth_app .
```

Set some variable for Domain, Traefik dashboard, IP Whitelistening:
```
export DOMAIN=.... TraefikPass=$(openssl passwd whoami) WhiteList="A, B, C"
WorkerIP=$(docker node inspect -f '{{ .Status.Addr }}' worker)
```

Initialize a swarm cluster:
```
docker swarm init
```

Create a registrty in order to required images be accessible from all nodes:
```
docker service create --name registry --publish published=5000,target=5000 registry:2
```
And push images sush as following:
```
docker image push 127.0.0.1:5000/auth_app
```

To deploy the stack:
```
docker stack deploy -c accounting.yml accounting
```
