# Generic Go HTTP/HTTPS Server


## Description

This Go-HTTP/HTTPS server implementation supports basic web-server features and simple configuration via a JSON file.

Use as is for a basic web server or adapt to your needs.

## Requirements

- [**Go**](https://go.dev/) 1.19 or newer

## Setup

### Expected folder structure

```
go-server/
 - *.go
 - cert,pem     (optional)
 - privkey.pem  (optional)
 - config.json
 - static/
   - css/
   - js/
   - img/
   - index.html
```

### Example config.json
```json
{
    "ORIGIN_URL": "localhost",
    "SERVER_PORT": "8000",
    "ENABLE_TLS": false,
    "CERT_FILE": "cert.pem",
    "PRIVATE_KEY_FILE": "privkey.pem"
}
```

| Key | default | description |
| :--: | :--: | -- |
| `ORIGIN_URL` | `"localhost"` |  |
| `SERVER_PORT` | `"8000"` | port the server is listening on |
| `ENABLE_TLS` | `"false"` | Should the server use HTTPS |
| `CERT_FILE` | `"cert.pem"` | Certificate file for use with HTTPS (optional) | 
| `PRIVATE_KEY_FILE` | `"privkey.pem"` | Private key file for use with HTTPS (optional) | 

## Running

### For testing
```
go run . 
```

### For deployment

#### Build the server for your platform
``` 
go build
```

#### Run the native binary
```
./go-server
``` 

---

### Tips for deployments

#### Use [**Caddy**](https://caddyserver.com/docs/) as a reverse proxy
Caddy allows you to host multiple HTTPS services from a single public IP.

Caddy supports automatic certificate application and renewal from [**letsencrypt.org**](https://letsencrypt.org/) allowing you to use HTTPS. When using caddy, run the server as HTTP (TLS off). Caddy wraps the service with TLS automatically.

#### A simple way to keep the server running in the background is to use *screen*
```
screen -S server -d -m ./go-online
```

The smarter way would be to run the server as a service
