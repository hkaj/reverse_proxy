# reverse_proxy


Reverse proxy using Traefik for all your container routing needs.

This configuration will automatically set up TLS for all your containers, expose metrics in the Prometheus format, and secure the administration interface behind htdigest.

Intended to be used with [media-server](https://github.com/hkaj/media-server/), but this setup is generic enough for many use cases.

# Use it

- create a `web` docker network (or rename the network in docker-compose.yaml): `docker network create web`
- in this repo's folder, run: `mkdir acme && touch acme/acme.json && chmod 600 acme/acme.json  # create an acme.json file where letsencrypt certs will be stored`
- `htdigest -c ht.digest traefik $USERNAME # you will be prompted for a new password`
- fill the `auth.digest` section in traefik.toml with the result of `cat ht.digest`. Traefik *will not start* without this step
- `DOMAIN_NAME=... ACME_EMAIL=... docker-compose up -d`
