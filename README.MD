# How To Create Docker Image

Docker has two ways to create a container image

- Create a Container, run several commands, and then use docker commit to generate a new image
- Create a Dockerfile and then use docker build to create an image

We are going to do the first step in this repo.

This topic is covered in Docker section in [DevOps in Depth]. In case you are interested in knowing more about the course you can check our website.


## Prerequisite

- Docker 1.13 and above
- Linux OS
- Basic Linux Knowledge

## Features

- Create a Container, run several commands, and then use docker commit to generate a new image

Create a Directory

```sh
mkdir docker-commit
```

cd to directory:
```sh
cd docker-commit
```
Create index.html file

```sh
cat <<EOF> index.html
<html>
<head>
<title>Welcome to my excellent blog</title></head>
<body bgcolor=blue>
<h1>Welcome to my blog</h1>
<h2>Jeeviacademy</h2>
</body>
</html>
EOF
```
View the file

```sh
cat index.html
```
Run httpd server
```sh
docker run -d -p 8080:80 --name httpserver httpd
```
Copy index.html into htdocs

```sh
docker cp index.html httpserver:/usr/local/apache2/htdocs
```
Check the running docker process

```sh
docker ps
```
## Docker ps output

>[root@lb1 docker-commit]# docker ps
>
>CONTAINER ID        IMAGE               COMMAND              CREATED             STATUS              PORTS                  NAMES
>
>21dd4b6e218b        httpd               "httpd-foreground"   57 seconds ago      Up 56 seconds       0.0.0.0:8080->80/tcp   httpserver

```sh
docker images
```
## Docker images output

>[root@lb1 docker-commit]# docker images
>
>REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
>
>docker.io/httpd     latest              6e794a483258        9 days ago          145 MB
>
>docker.io/alpine    latest              042a816809aa        2 weeks ago         7.05 MB
>
>docker.io/busybox   latest              66ba00ad3de8        3 weeks ago         4.87 MB
>[root@lb1 docker-commit]# 

Commit index.html into running container image

```sh
docker commit 21dd4b6e218b httpserver:v1
```
## Docker ps output

>[root@lb1 docker-commit]# docker ps
>
>CONTAINER ID        IMAGE               COMMAND              CREATED             STATUS              PORTS                  NAMES
>
>21dd4b6e218b        httpd               "httpd-foreground"   57 seconds ago      Up 56 seconds       0.0.0.0:8080->80/tcp   httpserver

Creating a new container from commited images
```sh
docker run -d -p 8081:80 --name httpd-v1 httpserver:v1
```
## Docker ps output

>[root@lb1 docker-commit]# docker ps
>
>CONTAINER ID        IMAGE               COMMAND              CREATED             STATUS              PORTS                  NAMES
>
>67b3a315bd4b        httpserver:v1       "httpd-foreground"   4 seconds ago       Up 3 seconds        0.0.0.0:8081->80/tcp   httpd-v1
>
>21dd4b6e218b        httpd               "httpd-foreground"   4 minutes ago       Up 4 minutes        0.0.0.0:8080->80/tcp   httpserver
>
>[root@lb1 docker-commit]# 

Check the website using Curl command

```sh
curl -vk localhost:8081
```
>
>[root@lb1 docker-commit]# curl -vk lb1.dev.com:8081
>* About to connect() to lb1.dev.com port 8081 (#0)
>*   Trying 127.0.1.1...
> Connected to lb1.dev.com (127.0.1.1) port 8081 (#0)
> GET / HTTP/1.1
> User-Agent: curl/7.29.0
> Host: lb1.dev.com:8081
> Accept: */*
> 
>< HTTP/1.1 200 OK
>< Date: Sat, 28 Jan 2023 04:59:45 GMT
>< Server: Apache/2.4.55 (Unix)
>< Last-Modified: Sat, 28 Jan 2023 04:51:24 GMT
>< ETag: "a0-5f34bbbe50b00"
>< Accept-Ranges: bytes< Content-Length: 160
>< Content-Type: text/html
>< 
<html>
<head>
<title>Welcome to Excellent Blog</title></head>
<body bgcolor=blue>
<h1>Welcom to my Excellent Blog</h1>
<h2>Deenadayalan M </h2>
</body>
</html>
* Connection #0 to host lb1.dev.com left intact

## License

MIT

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)
   [DevOps in Depth]: <https://www.jeeviacademy.com/devops-in-depth/>
   [Landrush]: <https://github.com/vagrant-landrush/landrush>
   [hostmanager]: <https://github.com/devopsgroup-io/vagrant-hostmanager>
   
