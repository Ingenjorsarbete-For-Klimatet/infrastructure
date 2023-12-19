# infrastructure

This repo contains IFKs infrastructure files, e.g. Dockerfiles for
servers etc.

To run this using docker-compose you need to clone this repo, `cd` to this folder and first enter the `client_id` and `client_secret` in the `.env` file

```bash
echo "CLIENT_ID=..." > .env
echo "CLIENT_SECRET=..." >> .env
```

You also need to create a GitHub PAT with the repo `read:packages` scope. Then, run

```bash
export CR_PAT=YOUR_TOKEN
```

and

```bash
echo $CR_PAT | docker login ghcr.io -u USERNAME --password-stdin
```

create a network

```bash
docker network create ifknet
```

and finaly

```bash
docker compose up
```

If the Nginx Proxy Manager (nginxpm) has not been initianlised before, you need to configure it for each service. In the future, we might keep all such config files in this repo (and not use nginxpm).

Custom configs for oauth (update `<app_host_name>` `<app_port>`)

```
location /auth {
    proxy_pass http://<app_host_name>:<app_port>;
    proxy_pass_request_headers      on;
    proxy_set_header   X-Real-IP        $remote_addr;
    proxy_set_header   X-Forwarded-For  $proxy_add_x_forwarded_for;
    proxy_set_header Early-Data $ssl_early_data;
}

location /callback {
    proxy_pass http://<app_host_name>:<app_port>;
    proxy_pass_request_headers      on;
    proxy_set_header   X-Real-IP        $remote_addr;
    proxy_set_header   X-Forwarded-For  $proxy_add_x_forwarded_for;
    proxy_set_header Early-Data $ssl_early_data;
}
```
