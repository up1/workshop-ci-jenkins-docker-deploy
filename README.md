# Workshop :: Deploy with Docker compose
* Frontend
  * ReactJS
* Backend
  * NodeJS
  * PostgreSQL

## Step 1 :: Start all containers

Set environment variables
```
$export FRONTEND_IMAGE=somkiat/frontend:1.0
$export BACKEND_IMAGE=somkiat/backend:1.0

$export FRONTEND_URL=http://host.docker.internal
$export FRONTEND_PORT=9999
```

Create all containers
* Frontend
* Backend
* Database

```
$docker compose up -d frontend

$docker compose ps
NAME                            IMAGE                  COMMAND                  SERVICE    CREATED          STATUS                    PORTS
workshop-02-deploy-backend-1    somkiat/backend:1.0    "docker-entrypoint.s…"   backend    18 seconds ago   Up 12 seconds (healthy)   3000/tcp
workshop-02-deploy-db-1         postgres:16.0          "docker-entrypoint.s…"   db         18 seconds ago   Up 18 seconds (healthy)   5432/tcp
workshop-02-deploy-frontend-1   somkiat/frontend:1.0   "/docker-entrypoint.…"   frontend   18 seconds ago   Up 6 seconds              0.0.0.0:9999->80/tcp

$docker compose logs --follow
```

Access in web browser with url
* http://localhost:9999
* http://localhost:9999/api/


## Step 2 :: Backend Testing with Postman
```
$docker compose up backend_test --abort-on-container-exit --build
```

## Step 3 :: Frontend Testing with Robot framework and Selenium
```
$docker compose up frontend_test --abort-on-container-exit --build
```

## Step 4 :: Delete all containers
```
$docker compose down
$docker volume prune
```
