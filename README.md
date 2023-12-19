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