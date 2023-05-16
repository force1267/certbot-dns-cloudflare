#  Certbot example with CloudFlare API in Docker

Sample config files to demonstrate seup that creates and updates free SSL certificates from [Let's Encrypt](https://letsencrypt.org/)
given that the domains are maintained at [CloudFlare](https://www.cloudflare.com/) service.

## How it works

[Certbot](https://certbot.eff.org/) verifies domains ownership by accessing CloudFlare API that adds temporary TXT DNS records. To enable it You must provide your CloudFlare [API token](https://developers.cloudflare.com/api/tokens/create). More details in [documentation](https://certbot-dns-cloudflare.readthedocs.io/en/stable/) for dns-cloudflare Certbot plugin.

Certbot saves created certificates in Docker volume `certbot_etc`. Pay attention to output of the certbot run - it mentions path to the created certificates.

## Steps to reproduce

1. Setup docker, docker-compose, domains, nginx – make your website work via plain HTTP.
2. change `docker-compose.yml` to add your domains.
3. `docker-compose run certbot` to create certificates. It will wait for 60 seconds in the middle. Note the output of the command – it will contain actual paths to certificates.
4. certificates are in `certs` directory.

## refs
https://gist.github.com/sergiks/4c1ccddc097e61e6fe5e45c53072a944
