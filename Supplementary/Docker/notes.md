# Docker

## Facts
- Docker Compose is a tool to run multiple containers together.
- Docker Compose does not auto rebuild production builds, it only runs dev servers with volume-mounted code that hot reloads.
- Hot reload means a development server watches source files and updates the app instantly without rebuilding.
- Volumes sync files into the container, hot reload is done by the dev server.
- Without volumes, hot reload does not work in Docker dev environments.
- <docker-compose.yml> is used to define and run multiple Docker containers together.
- If building locally, you do not need `docker login`. If building and pushing to Docker Hub or another registry, you must first run `docker login`, then use `docker push username/myapp:latest` to push the built image.
- Package manager, Node.js, and Docker version mismatches can cause dependency conflicts and deployment build failures due to different environment behaviors.
- Our source code are stored inside docker environment, usually inside nginx container at: `/var/www/html`. So even if the frontend code exists on local machine, the app actually runs inside docker container environment. That is why dependencies sometimes need to install inside container instead of local machine.
- When running Next.js in Docker (especially on WSL2/Docker Desktop), newly created routes may return 404 because filesystem events from mounted volumes are not reliably propagated to Watchpack. Even restarting containers may not resolve the issue. Setting ```WATCHPACK_POLLING=true``` at `docker-compose.yml` `environment` forces Watchpack to poll the filesystem, ensuring new routes are detected and preventing unexpected 404 errors.

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


