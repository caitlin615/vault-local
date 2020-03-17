vault-local
---

Running vault in docker with auto-unseal abilities so you can re-run it
and not lose data when the docker image is stopped.

```bash
# Start
docker-compose up -d

# Stop
docker-compose down

# Logs
docker-compose logs

# Access CLI
docker-compose exec vault-dev sh
```

You can access vault via `http://localhost:8200` and can log in with the `VAULT_DEV_ROOT_TOKEN_ID`
in the docker-compose.yml file.

```
export VAULT_TOKEN=${VAULT_DEV_ROOT_TOKEN_ID from docker-compose.yml}`
export VAULT_ADDR='http://127.0.0.1:8200'
```

See `unseal/sealfile` for the output from vault to get the root token and unseal key.

# Reset
To clean up vault and start over:
```
docker-compose down
rm -rf vault unseal
docker-compose up -d
```
