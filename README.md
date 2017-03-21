# reverse_proxy


Reverse proxy using Traefik for all your container routing needs.

This configuration will automatically set up TLS for all your containers.

Intended to be used with [media-server](https://github.com/hkaj/media-server/), but this setup should be generic enough for lots of use cases.

# To run
- ADMIN_PORT=... DOCKER_DOMAIN=... ACME_EMAIL=... docker-compose up -d
