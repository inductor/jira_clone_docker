# JIRA Clone Docker

This is a ready-for-docker version of [JIRA Clone](https://github.com/oldboyxx/jira_clone/).

This project does not completely work yet, but you can try it out by executing

```bash
docker-compose up -d --build
```

BuildKit is recommended for concurrent build. If enabled on your Docker environment, execute as follows instead.

```bash
COMPOSE_DOCKER_CLI_BUILD=1 docker-compose up -d --build
```
