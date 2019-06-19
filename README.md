# NGINX SSL Proxy

This repository holds example implementations of [NGINX SSL Proxy](https://github.com/DanielDent/docker-nginx-ssl-proxy) by [DanielDent](https://github.com/DanielDent).

## Volumes

### Configuration Files

- Base module configuration location
  `/etc/nginx/conf.d/default.conf`

- Extension module configuration location
  `/etc/nginx/main_location.conf`

Use a Dockerfile to place your configuration files inside.

### Certificate data

- An account_key.json file holds the key to your Let's Encrypt account - which provides a convenient way to revoke a certificate.
- Recommended use of a docker volume in for backup and access inside the other containers that may need those certificates
  `letsencrypt:/etc/letsencrypt`

## Environment Variables

| Variable         | Required | Description                                                                                                                                                                  |
| :--------------- | :------: | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SERVERNAME       |    X     | The hostname to listen to. The system will automatically obtain an SSL certificate for this hostname.                                                                        |
| HSTS_HEADER      |          | Can be disabled if set to `skip`. [HSTS Strict-Transport-Security Header](https://hub.docker.com/r/danieldent/nginx-ssl-proxy#WARNING-HSTS-Strict-Transport-Security-Header) |
| SECURITY_HEADERS |          | Can be disabled if set to `skip`.                                                                                                                                            |

## SSL settings warnings

### Cyphers

Reasonable defaults have been chosen by [danieldent](https://hub.docker.com/u/danieldent/) for SSL cipher suites using Mozilla's Recommendations. Very old browsers (such as IE6) will be unable to connect with the default settings.

### Security Headers

If your upstream server is already sending these headers, setting the SECURITY_HEADERS variable will avoid the presence of multiple instances of these headers in responses.
These headers can be disabled by setting the SECURITY_HEADERS variable to skip.
See https://www.owasp.org/index.php/List_of_useful_HTTP_headers for more information on the headers used or to test your domain.
