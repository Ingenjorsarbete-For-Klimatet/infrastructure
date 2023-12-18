# oauth

This dockerfile packages the oauth script. To run this using docker-compose you need to clone this repo, `cd` to this folder and first enter the `client_id` and `client_secret` in their respective files (`client_id` and `client_secret`) under a `secret` folder. Then, run

```bash
docker compose up
```