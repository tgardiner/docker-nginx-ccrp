# docker-nginx-ccrp

## About

Work around CORS issues by running an Nginx reverse proxy that will cache requests to the source API.

## Requirements

* Docker

## Configuration

Check the serverblock inside `default.conf`.  At a minimum you'll need to change the [destination address](default.conf#L4).

The config has a [10s cache expiry](default.conf#L13) and some options to hide certain headers from the response.

See the Nginx documentation [here](https://nginx.org/en/docs/http/ngx_http_proxy_module.html).

## Build

```bash
docker build -t nginx-ccrp .
```

## Run

```bash
docker run -dit --name nginx-ccrp -p 8080:80 nginx-ccrp
```

## Test

Requests to http://localhost:8080/ should return your configured API.
