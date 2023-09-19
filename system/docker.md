# Docker

Documentation made by Shisuko

*** 

## Summary

1. What's docker ?
2. How to install it on different plateforme   
2.1 Install docker on debian base   
2.2 Install docker on windows
3. How to use it ?
4. Install MySQL with docker

## 1. What's docker ? 

Docker is a software that can install software with his proper environnement (linux based). It's make easier to install/manage/delete services on a server for example. Docker doesn't use virtual elements, he use the hardware of his host. So it make him faster and stronger that a virtual machine.

## 2. Install docker on different plateforme

### 2.1 Install docker on debian base

To install it on debian base just use apt : 

```bash
sudo apt install docker
```

Depend on the version of your debian you may want to use this :   

https://docs.docker.com/engine/install/debian/

### 2.2 Install docker on windows

To install it on windows just go to docker official website and download the .exe file :
https://www.docker.com/

Lauch it and do the basic installation.

## 3. How to use it ?

To use docker just open a terminal. And type :   
(It's the same command for windows/linux just don't use the sudo on windows)

```bash
sudo docker --help
```

It will display the docker help.

To install a service with docker you need to download the image, you can go on docker hub to find the image that you want. To download it just use the pull command.

```bash
sudo docker pull image:flag
```

The image is the image of the service that you want to pull, and the flag is basicly the version of the image that you want to download. If you don't put any flag, it will install the latest version.

After downloading the image you need to create a docker instance, it will create the environnement for the service and the service. To do it use the run command.

```bash
sudo docker run --name <name_of_your_instance> --restart=<when_the_service_need_to_restart> -d <name_of_the_image>
```

What this command does ? It create a instance with a name and config the condition for the instance to restart. The '-d' is for --detach, it make the container to run in the backgroud.

If you don't know the name of your image you can type this command :

```bash
sudo docker images
```

And you have install a docker container, bravo ! Now we are going to install MySQL to make a example.

## 4. Install MySQL with docker

First of all we need to download the image of mysql to do this run this command : 

```bash
sudo docker pull mysql
```

After this we will need to create the instance for the mysql container. To do this run this command :

```bash
sudo docker run --name mysql --restart=on-failure -p 10.205.201.110:3306:3306 -e MYSQL_ROOT_PASSWORD=1234 -d mysql
```

We add a thew paramets let me explain... 

The -p is for the ip that your container will have. So when you are going to connect into the database you will type "10.205.201.110" the first port (pc port to the container) is the external port, and the second is the internal port (container port to the service).

The -e is for environnement variable. Here we add a password for the root.

After create the instance we can connect to the database. But before we can check if the container is running.

```bash
sudo docker ps -a
```

If the container is not running type this command :

```bash
sudo docker start mysql
```

To connect to the database use this command :

```bash
sudo docker exec -it mysql mysql -u root -p
```

To explain the command : 

We execute a command into our container the command is : 

```bash
mysql -u root -p
```

And the command :

```
sudo docker exec -it mysql
```

Is for executing a command into our container.

After being connect into the database you can change the password with this command : 

```sql
alter user 'root'@'localhost' identified by 'Pa$$w0rd';
```

To apply the modification just type this command to restart the container : 

```bash
sudo docker restart mysql
```

And there you have installed a docker container for mysql !

***

Twitter : @Shisukkko
