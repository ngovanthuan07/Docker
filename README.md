# Docker
# Làm việc với spring boot
```
docker build -t springboot-docker . 
```

```
docker images
```

```
docker image ls
```

```
docker tag  springboot-docker:latest springboot-docker:v1.0.0
```

```
docker tag springboot-docker:v1.0.0 ngovanthuan07/springboot-docker:v1.0.0
```

```
docker push ngovanthuan07/springboot-docker:v1.0.0
```

```
docker rmi -f <image>
```

```
docker run -dp 8085:8083 --name springboot-docker-container -v "$(pwd):/app" ngovanthuan07/springboot-docker:v1.0.0
```
