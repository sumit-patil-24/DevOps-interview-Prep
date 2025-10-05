# how to copy files to docker container ?

## The general syntax for copying files from your host machine into a container is:
```
docker cp [HOST_PATH] [CONTAINER_NAME_OR_ID]:[CONTAINER_PATH]

example:
docker cp local_file.txt my_container:/path/in/container/
```


## Reverse Copy: You can also copy files out of the container back to your host machine by simply reversing the paths:
```
docker cp my_container:/var/log/app.log /home/user/logs/
```


#📝 Key Considerations
## Container State: The container must be running or at least stopped for the command to work. It cannot be in a removed state.

## Permissions: Files copied into the container will inherit the permissions of the user running the Docker daemon (usually root inside the container).

