# Postgres

## Upgrade a Postgres container

To upgrade the database:
* Create new pgdata directory for the new database
* Create database container using new postgres, and pointing to the new data directory
* Stop all of the containers
  ```docker compose stop --remove-orphans```
* Start the 2 database containers (change container names to match)
  ```docker compose up db16 db17 -d```
* Run pgdbcopy (change container names to match)
  ```docker run --rm --network ctr-network -it ghcr.io/dimitri/pgcopydb:latest pgcopydb clone --source postgresql://paperless:paperless@db16/paperless --target postgresql://paperless:paperless@db17/paperless --dir /tmp```
* Stop containers
  ```docker compose stop --remove-orphans```
* Update service to point to new container
* Comment out old container (verifies it isn't being used)
* Start all containers
  ```docker compose up -d```
* Verify service is working.
* Delete old database