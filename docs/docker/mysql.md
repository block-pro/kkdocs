# docker mysql

## docker run mysql

```bash
docker run --name mysql-dy-01 -p 3306:3306 -v /home/kkqiao/data/mysql/mysql-dy-01:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=Aa651830 -d mysql:5.7
```

## Connect to MySQL from the MySQL command line client

```bash
docker run -it --rm mysql mysql -hsome-mysql -uexample-user -p

alias mysql='sudo docker run -it --rm mysql mysql'

mysql -h172.17.0.1 -u root -p
```

## create table

```mysql
create database dybarrage_pro;
set GLOBAL max_connections=200;
```

## node test

```bash
docker run --rm -it node bash
git clone https://github.com/Crawler995/DouyuBarrage-Pro.git
sed -i '2s/localhost/172.17.0.1/' /DouyuBarrage-Pro/dybarrage-server/src/config.ts
sed -i '4s/crawler995/Aa651830/' /DouyuBarrage-Pro/dybarrage-server/src/config.ts
npm install cross-env -g
npm install react-app-rewired -g
```

## dy dockerfile

```Dockerfile
FROM node

RUN npm install cross-env -g && \
    npm install react-app-rewired -g

COPY DouyuBarrage-Pro/ /DouyuBarrage-Pro
COPY start.sh /
RUN chmod +x start.sh

RUN sed -i '2s/localhost/172.17.0.1/' /DouyuBarrage-Pro/dybarrage-server/src/config.ts && \
    sed -i '4s/crawler995/Aa651830/' /DouyuBarrage-Pro/dybarrage-server/src/config.ts

EXPOSE 3000
EXPOSE 3001

ENTRYPOINT ["/bin/bash","/start.sh"]

```

## dy docker build

```bash
docker build -t kk-douyu-barrage-pro:200630 .
```

## dy docker run

```bash
docker run --name dy-barrage-200630 -d \
    -p 3000:3000 \
    -p 3001:3001 \
    kk-douyu-barrage-pro:200629
```

```bash
docker run --rm -it \
    -p 3000:3000 \
    -p 3001:3001 \
    kk-douyu-barrage-pro:200630 \
    bash
```

## reference

* <https://hub.docker.com/_/mysql>
