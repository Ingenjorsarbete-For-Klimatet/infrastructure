# oauth

This dockerfile packages the oauth script. To run this using docker-compose you need to clone this repo, `cd` to this folder and first enter the `client_id` and `client_secret` in their respective files (`client_id` and `client_secret`) under a `secrets` folder. 

You also need to create a GitHub PAT with the repo `read:packages` scope. Then, run

```bash
export CR_PAT=YOUR_TOKEN
```

and

```bash
echo $CR_PAT | docker login ghcr.io -u USERNAME --password-stdin
```

and finaly

```bash
docker compose up
```