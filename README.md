# services
My list of selfhosted services.

## Usage

1. Start `traefik`

[traefik](https://traefik.io/traefik/) is a dynamic reverse-proxy that autodetects running microservices (via Docker labels) and exposes them. It will expose each microservice automatically.
```
cd traefik
docker-compose up -d
```

2. Run any other services you want (i.e. pihole)
> **Note** Most services need a `.env` file where environment variables are defined. Check the documentation of each image for the required variables.
```
cd pihole
docker-compose up -d
```

3. Edit your `/etc/hosts` by adding a mapping from `SERVICE.localhost` to `127.0.0.1`:
```
...
127.0.0.1	pihole.localhost
127.0.0.1	jupyter.localhost
...
```
Not all services work with path-prefix redirection. Subdomain-based redirection works out of the box on the other hand but needs manually pointing the subdomain to localhost.