# maxbublik_platform
maxbublik Platform repository


## kubernetes-intro

```
docker build -t codecomrade/otus-kuber:kubernetes-intro -f kubernetes-intro/web/Dockerfile kubernetes-intro/web
docker push codecomrade/otus-kuber:kubernetes-intro
```

## kubernetes-intro (Сборка Hipster shop)

```
git clone git@github.com:GoogleCloudPlatform/microservices-demo.git microservices-demo
cd microservices-demo/src/frontend
docker build -t codecomrade/otus-kuber:microservices-demo-frontend .
docker push codecomrade/otus-kuber:microservices-demo-frontend
```
