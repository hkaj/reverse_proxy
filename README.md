# reverse_proxy


Reverse proxy using Traefik for all your container routing needs.

This configuration will automatically set up TLS for all your containers.

Intended to be used with [media-server](https://github.com/hkaj/media-server/), but this setup should be generic enough for lots of use cases.

# To run
Copy .env.tempalte to .env

  `cp .env.tempalte .env`

Edit .env variables:

  `vim .env` or `nano .env`
  
Start docker-compose

  `docker-compose up -d`
