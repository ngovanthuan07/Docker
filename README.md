# Docker
# Làm việc với spring boot
🐱‍🚀 Xem toàn bộ container
```
docker ps -a
```

```
docker build -t springboot-docker . 
```

```
docker images
```

```
docker image ls
```
😆 Thay dổi tên 1 image
```
docker tag  springboot-docker:latest springboot-docker:v1.0.0
```
🐱‍👓 Liên kết với docker hub
```
docker tag springboot-docker:v1.0.0 ngovanthuan07/springboot-docker:v1.0.0
```

```
docker push ngovanthuan07/springboot-docker:v1.0.0
```
🙃 Xoá một image
```
docker rmi -f <image>
```
😉
```
docker run -dp 8085:8083 --name springboot-docker-container -v "$(pwd):/app" ngovanthuan07/springboot-docker:v1.0.0
```
😫
```
docker restart springboot-docker-container
```
😁 Tạo một network
```
docker network create springboot-app-network
```
😍 Xem tất cả network
```
docker network ls
```
🧐 Xem full option netwrork
```
docker network
```
😸
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
👏 Xoá một container
```
docker rm -f springboot-docker-container
```

😜 Thiết lập cùng chung network
```
docker run -dp 8085:8083 `
     --name springboot-docker-container `
     -v "$(pwd):/app" `
     --network springboot-app-network `
     ngovanthuan07/springboot-docker:v1.0.0
```
😀
```
docker exec -it mysql-springboot-container mysql -u root -p
```
```
SHOW DATABASES;
```
```
use doanphanmem1;
```
```
show tables;
```
🍗🍗🍗🍗🍗 Bây giờ thực hiện câu truy vấn như trong sql vd: select * from HocVan;

🤔 Xem một container đang chạy
```
docker logs springboot-docker-container
```

```
docker rm -f mysql-springboot-container springboot-docker-container
```
```
docker-compose  -f docker-compose.dev.yml up --build
```
😳 docker-compose
```
version: '3.8'

services:
  mysql-springboot-container:
    image:  mysql:8.0.28
    container_name: mysql-springboot-container
    posts:
      - 3310:3306
    volumes:
      - mysql-springboot-data:/var/lib/mysql
      - mysql-springboot-config-deamond:/etc/mysql/conf.d
    networks:
      - backend
    environment:
      MYSQL_USER: thuan 
      MYSQL_PASSWORD: 12345678 
      MYSQL_ROOT_PASSWORD: 12345678 
      MYSQL_DATABASE: doanphanmem1 
  springboot-docker-container:
    image: ngovanthuan07/springboot-docker:v1.0.0
    container_name: springboot-docker-container
    ports:
      - 8085:8083
    volumes:
      - ./:/app
    networks:
      - backend
#create network
networks:
  backend:
    name: springboot-app-network
volumes:
  mysql-springboot-data:
  mysql-springboot-config-deamond:
```
