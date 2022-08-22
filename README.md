# Rasa Chatbot Hackathon
Here are the files for creating the chatbot model.  

## Using Docker for Rasa
[Building a Rasa Assistant in Docker](https://rasa.com/docs/rasa/docker/building-in-docker/)

```
$ docker -v

$ mkdir Docker

$ cd ~/Docker

$ mkdir rasa

$ cd rasa
```

## ECS computer and using Docker Desktop and Gitbash
NOTE: Before you run the first docker command, DISCONNECT from the ECS VPN - this docker image is rather large (>2GB) and the network will 
throttle you and the download will take FOREVER, meaning never finish.  Once you disconnect from the VPN, the download of the image will speed up greatly.  This is what the IT Help Desk told me to do, so it is permissible.  Just after running the first docker command, reconnect to the VPN.

In order to get Rasa Docker working, you need a number of additional values

To get your userid
```
$ id -u Firstname.Lastname
```

To get your groupid
```
$ id -g Firstname.Lastname
```

To get the current directory where you are installing Rasa docker to format should be "c/Users/Firstname.Lastname/dockerdirectory" if there are spaces in the path, make sure to use quotation marks
```
$ pwd
```

The **--mount src="/c/Users/Firstname.Lastname/pathtorasa/",dst=/app,type=bind** parameter in the commands binds your local directory to the docker containers path, so docker must run with you as the owner in order for you to be able to write/edit files in this bound directory.  If you don't include this, you will not be able to save changes to any of the files in this directory and the training will also fail.

To setup Rasa for the first time
```
docker run -u 1089705:1049089 --mount src="/c/Users/Firstname.Lastname/pathtorasa/",dst=/app,type=bind rasa/rasa:3.2.6-full init --no-prompt
```

To train Rasa 
```
docker run -u 1089705:1049089 --mount src="/c/Users/Richard.Torzynski/Docker/rasa/",dst=/app,type=bind rasa/rasa:3.2.6-full train --domain domain.yml --data data --out models
```

To use Rasa Shell and custom actions, add a new network
```
docker network create my-project
```

To use Rasa Shell, make sure to add winpty before the command or you'll get an error
```
$ winpty docker run -u 1089705:1049089 -it --mount src="/c/Users/Richard.Torzynski/Docker/rasa/",dst=/app,type=bind -p 5005:5005 --net my-project rasa/rasa:3.2.6-full shellgit 
```

To use custom actions, need to start the Rasa Action Server
```
docker run -u 1089705:1049089 -d --mount src="/c/Users/Richard.Torzynski/Docker/rasa/",dst=/app/actions,type=bind --net my-project --name action-server rasa/rasa-sdk:3.2.0
```
## Docker commands

Stop the action server
```
docker stop action-server
```

List running docker containers
```
docker ps
```

List local docker images
```
docker images
```

Remove local docker image
```
docker rm image image-to-remove
```

Stop docker container
```
docker stop [container-id]
docker stop [container-name]
```

## Git Commands

Initialize the local Git repository
```
git init
```

Connect to the Rasa Chatbot Hackathon Repo
```
git remote add origin https://github.com/ecsricktorzynski/rasa-chatbot-hackathon.git
```

Check to see if connection made
```
git remote -v
```

Create a docker branch
git checkout -b dockerls -la


Create a main branchgcd
git checkout -b main
