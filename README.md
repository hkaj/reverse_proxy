# reverse_proxy


Reverse proxy using Traefik for all your container routing needs.

This configuration will automatically set up TLS for all your containers, and secure the administration interface behind htdigest.

Intended to be used with [media-server](https://github.com/420m/media-server/), but this setup is generic enough for many use cases.

It requires that you own a public domain that you can point at your server's IP.

By default we use the HTTP challenge for LetsEncrypt, however if your server IP is not exposed to the internet (e.g. behind a VPN), you'll need to fallback to the DNS challenge.

# Use it

- create a `web` docker network (or rename the network in docker-compose.yaml): `docker network create web`
- `htdigest -c ht.digest traefik $USERNAME # you will be prompted for a new password`
- fill the `digestAuth` label in docker-compose.yaml with the result of `cat ht.digest`. Traefik *will not start* without this step
- configure an A record in your registrar to point `@` and `*` (the name and all its subdomains) to your server's IP
- if your server's IP is routable over the internet, run `DOMAIN_NAME=... ACME_EMAIL=... docker compose up -d`
- if not (e.g. using a VPN), comment the http challenge settings and uncomment the DNS ones + add the required env variables for your registrar. E.g. for Gandi, uncomment the `environment` section and run this command: `GANDI_API_KEY=... DOMAIN_NAME=... ACME_EMAIL=... docker compose up -d`
