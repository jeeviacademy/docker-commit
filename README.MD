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
>[root@lb1 docker-commit]# docker ps
>
>CONTAINER ID        IMAGE               COMMAND              CREATED             STATUS              PORTS                  NAMES
>
>21dd4b6e218b        httpd               "httpd-foreground"   57 seconds ago      Up 56 seconds       0.0.0.0:8080->80/tcp   httpserver


## License

MIT

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)
   [DevOps in Depth]: <https://www.jeeviacademy.com/devops-in-depth/>
   [Landrush]: <https://github.com/vagrant-landrush/landrush>
   [hostmanager]: <https://github.com/devopsgroup-io/vagrant-hostmanager>
   
