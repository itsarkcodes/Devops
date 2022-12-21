**Docker Version:** ```docker -version```

**Pull Docker image from repository:** ```docker pull ubuntu```

**To make a container from image:**```docker run -it <image-name>```

Example: ```docker run -d myubuntu```
> -d : Detached mode,  It is used to run the container in the background and print container ID. 
> 
> Referenc: https://www.educba.com/docker-run-command/

**Display all running process** : ```docker ps -a``` 

**Kill a container**:```docker kill <container id>```

> Example:```docker kill d61153bc``` 

**List all the images**:```docker images```


