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

To setup Rasa for the first time
```
$ docker run --mount src="/c/Users/Firstname.Lastname/pathtorasa/",dst=/app,type=bind rasa/rasa:3.2.6-full init --no-prompt
```

So for me where I created a directory 
```
docker run --mount src="/c/Users/Richard.Torzynski/Docker/rasa/",dst=/app,type=bind rasa/rasa:3.2.6-full init --no-prompt
```

If you get a error message about permissions, try adding -u userid:groupid to the above command.
```
$ docker run -u 1089705:1049089 --mount src="/c/Users/Richard.Torzynski/Docker/rasa/",dst=/app,type=bind rasa/rasa:3.2.6-full init --no-prompt
```

To train Rasa 
```
$ docker run -u 1089705:1049089 --mount src="/c/Users/Richard.Torzynski/Docker/rasa/",dst=/app,type=bind rasa/rasa:3.2.6-full train
```

To use Rasa Shell, make sure to add winpty before the command or you'll get an error
```
$ winpty docker run -u 1089705:1049089 -it --mount src="/c/Users/Richard.Torzynski/Docker/rasa/",dst=/app,type=bind -p 5005:5005 --net my-project rasa/rasa:3.2.6-full shell
```

## Docker commands

Stop the action server
```
$ docker stop action-server
```

List running docker containers
```
$ docker ps
```

List local docker images
```
$ docker images
```

Remove local docker image
```
$ docker rm image image-to-remove
```

Stop docker container
```
$ docker stop [container-id]
$ docker stop [container-name]
```
