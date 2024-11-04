# Steps to Learn docker container

## MongoDB Container

### Pull Mongo Container

```
docker pull mongo
```

### Create an image 

```
docker build -t mongodb mongo
```

### Run Container

```
docker run --name mongodb -v data:/data/db -e MONGO_INITDB_ROOT_USERNAME=neeraj -e MONGO_INITDB_ROOT_PASSWORD=raviteja --rm -d --network goals-network mongo
```

## Backend Container

### Create an image 

```
docker build -t goals-node .
```

### Run Container

```
docker run --name goals-backend -v /Users/neerajsarathe/Documents/Others/multi-01-starting-setup/backend:/app  -v logs:/app/logs -d --network goals-network -v logs:/app/logs --rm -p 80:80 goals-node
```

## Frontend Container

### Create an image

```
docker build -t goals-react .
```

### Run Container

```
docker run -v /Users/neerajsarathe/Documents/Others/multi-01-starting-setup/frontend/src:/app/src --name goals-frontend --rm -d -p 3000:3000 goals-react
```

# Alternate Approach
## Using Docker Compose

### To start a docker
```
docker compose up # For Docker Desktop
docker-compose up # For Docker CLI
```

#### Arguments:
- \-d : To run docker in dettached mode
- \--build : To force rebuild all the images on every start

### To stop the container

```
docker compose down # For Docker Desktop
docker-compose down # For Docker CLI
```

#### Arguments: 
- \-v : To delete volumes when the containers are stopped


#### Points to Remember:
- Networks is by default created once the docker is up unless you need a custom network for specific task
- On docker-compose down, all the containers and networks are deleted automatically

> **_NOTE:_**
> This multi container setup is used for the development environment