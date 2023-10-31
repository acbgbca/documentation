# Docker

## Compose

### Set User

To run a container as a specific user, add the following:
```
services:
  app:
    user: "${UID}:${GID}"
```
Where ${UID} and ${GID} are the user and group IDs respectively.

### Healthcheck
```
services:
  app:
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:8080/healthcheck"]
      interval: 1m
      timeout: 10s
      retries: 3
      start_period: 1m
```
test: The command to run. Must be a command available in the container.
inverval: How often to run the check
retries: How many time can this fail before the container is considered bad
start_period: How long should we wait after starting the container to run the first check

### External Network
Required to allow communication between Docker stacks. Must be manually created in Docker
```
networks:
  default:
    external: true
    name: ctr-network
```

### Internal only network
Creates an internal only network. I.e. It can not connect to the internet.

Useful for databases and similar containers that only need to be available internally
```
networks:
  internal:
    driver: bridge
    internal: true
    name: internal
```

To connect to multiple networks in a serviec:
```
services:
  app:
    networks:
      - internal
      - default
```