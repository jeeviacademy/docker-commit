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
cp Vagrantfile .
```

Run Vagrant up Command to bring up 3 VM

```sh
vagrant up
```
To check the status of the machine
```sh
vagrant status
```
Other Vagrant Commands

```sh
vagrant global-status
vagrant port lb1
vagrant port web1
```


## License

MIT

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)
   [DevOps in Depth]: <https://www.jeeviacademy.com/devops-in-depth/>
   [Landrush]: <https://github.com/vagrant-landrush/landrush>
   [hostmanager]: <https://github.com/devopsgroup-io/vagrant-hostmanager>
   
