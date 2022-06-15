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
```
docker restart springboot-docker-container
```

```
docker network create springboot-app-network
```

```
docker network ls
```
Xem full option netwrork
```
docker network
```

```
docker run --rm -d `
     -v mysql-springboot-data:/var/lib/mysql `
     -v mysql-springboot-config-deamond:/etc/mysql/conf.d `
     --name mysql-springboot-container `
     -p 3310:3306 `
     -e MYSQL_USER=thuan `
     -e MYSQL_PASSWORD=12345678 `
     -e MYSQL_ROOT_PASSWORD=12345678 `
     -e MYSQL_DATABASE=doanphanmem1 `
     --network springboot-app-network `
     mysql:8.0.28
```
