# Airlance

This is local stack for developers. Check out instructions below to getting started.

## Prerequires

To work with this repository you should install docker and node.js
Checkout instructions how to install it on your operating system.

Docker: https://docs.docker.com/engine/install/
Node.js: https://nodejs.org/en/download/

## Setup local environment

Clone this repository
Go to directory hygiene
Run the following commands:

```
npm install
make services-init
make projects-init
make services-deploy
```

On the output you can see all projects domains.

Use command `make help` to get all available commands.

### Create a local proxy

Run the following commands if you use brew on mac or use `/opt/homebrew/etc/nginx/`:

```
sudo mkdir /opt/homebrew/etc/nginx/hygiene.d
sudo make dns
```
Type the directory location with trailing slash: `/opt/homebrew/etc/nginx/hygiene.d/`
than reload nginx: `sudo nginx -s reload`

Update your `/opt/homebrew/etc/nginx/nginx.conf` file, add line `include hygiene.d/*.conf;` to section http.

After that add next rows to your `/etc/hosts` file

```
127.0.0.1    api.hygiene.localhost
127.0.0.1    rabbitmq.hygiene.localhost
127.0.0.1    adminer.hygiene.localhost
127.0.0.1    minio.hygiene.localhost
```

If all done correctly, you should had access to all hosts above via your browser.

### Local passwords

http://adminer.hygiene.localhost hygiene/hygiene
http://rabbitmq.hygiene.localhost hygiene/hygiene
http://minio.hygiene.localhost hygiene_user/hygiene_password