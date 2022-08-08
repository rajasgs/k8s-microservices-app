# k8s-microservices-app

Simple app that connects front end with back end and acts as a micro service.
Front end serves the backend through backend consumer. App can be run using the docker compose file in deployment-docker or using kubernetes (kind).

## Running locally

```
cd frontend
python3 app.py

cd backend
python3 app.py
```

## Dockerization

```
docker network create pr_network
```
verify the docker network
```
docker network ls | grep pr_network
```

```
cd deployment-docker
docker-compose up --build
```


## Kubernization

```
kind create cluster --name pr-k8s
```

```
docker build -t pr-be ../backend/
docker build -t pr-fe ../frontend/
```

```
kind load docker-image pr-fe --name pr-k8s
kind load docker-image pr-be --name pr-k8s

```


```
kubectl apply -f k8s
```

```
kubectl port-forward svc/pr-fe 9090:80
```

changes in the code

```
docker build -t pr-fe../frontend/

kind load docker-image pr-fe --name pr-k8s

kubectl rollout restart deployment/pr-fe

kubectl port-forward svc/fin-ui 9090:80
```
