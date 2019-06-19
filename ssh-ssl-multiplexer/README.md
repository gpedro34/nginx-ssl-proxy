# SSH and SSL multiplexer

## Features

## Environment Variables

| Variable         | Required | Description                                                                                                                                                                  |
| :--------------- | :------: | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SERVERNAME       |    X     | The hostname to listen to. The system will automatically obtain an SSL certificate for this hostname                                                                         |
| SSH              |          | The IP address or hostname (and optional port) of the SSH server to proxy requests towards                                                                                   |
| WEB              |          | The IP address or hostname (and optional port) of the web server to proxy requests towards                                                                                   |
| HSTS_HEADER      |          | Can be disabled if set to `skip`. [HSTS Strict-Transport-Security Header](https://hub.docker.com/r/danieldent/nginx-ssl-proxy#WARNING-HSTS-Strict-Transport-Security-Header) |
| SECURITY_HEADERS |          | Can be disabled if set to `skip`.                                                                                                                                            |
