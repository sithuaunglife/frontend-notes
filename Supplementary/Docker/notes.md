# Docker

## Facts
- Docker Compose is a tool to run multiple containers together.
- Docker Compose does not auto rebuild production builds, it only runs dev servers with volume-mounted code that hot reloads.
- Hot reload means a development server watches source files and updates the app instantly without rebuilding.
- Volumes sync files into the container, hot reload is done by the dev server.
- Without volumes, hot reload does not work in Docker dev environments.
- <docker-compose.yml> is used to define and run multiple Docker containers together.
- If building locally, you do not need `docker login`. If building and pushing to Docker Hub or another registry, you must first run `docker login`, then use `docker push username/myapp:latest` to push the built image.

## Syntax
**Heading**
```js 
 <!-- code here -->
```
- Description

## Terminal Commands
### Docker

**Docker compose run**
```bash
docker compose up
```
- It run the docker compose.


**Docker compose run in detach mode**
```bash
docker compose up -d
```
- It run the docker compose in detach mode.

 
**Docker compose stop**
```bash
docker compose down
```
- It stop the docker compose. It is used with docker compose running in detached mode not normal docker compose run.


**Docker compose run and build**
```bash
docker compose up --build
```
- It run the docker compose and build. ```--build``` is needed when image-related things changed. 


**Multi-arch build (AMD64 target)**
```bash
docker buildx build \
  --platform linux/amd64 \
  -t myapp:latest \
  --push .
```
- ```--push``` → sends directly to registry
- ```-t``` already tags the image
- useful for CI/CD
- common in Coolify workflows

## Tools
- Notes


