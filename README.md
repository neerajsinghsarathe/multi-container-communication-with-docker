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