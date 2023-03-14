
<img style="margin-left: -80px" src="https://d1.awsstatic.com/acs/characters/Logos/Docker-Logo_Horizontel_279x131.b8a5c41e56b77706656d61080f6a0217a3ba356d.png"/>

# **`Docker`**
## `I> Overall`
### `1.1. Introduction`
Docker is a software platform that allows you to build, test, and deploy applications quickly. Docker packages software into standardized units called containers that have everything the software needs to run including libraries, system tools, code, and runtime. Using Docker, you can quickly deploy and scale applications into any environment and know your code will run.

### `1.2. Benefit when using docker`
- Fast, consistent delivery of your applications
- Responsive deployment and scaling
- Running more workloads on the same hardware

### `1.3. Docker architecture`
<img style="margin: 0 auto" src="https://docs.docker.com/assets/images/architecture.svg">

### `1.4. Docker objects`
When you use Docker, you are creating and using images, containers, networks, volumes, plugins, and other objects. This section is a brief overview of some of those objects. Two Object is often used in docker is image and container

`Image:` An image is a read-only template with instructions for creating a Docker container. Often, an image is based on another image, with some additional customization. 

`Container:` A container is a runnable instance of an image. You can create, start, stop, move, or delete a container using the Docker API or CLI. You can connect a container to one or more networks, attach storage to it, or even create a new image based on its current state.

`Network:` When working with docker we want to connect each service together or prevent some service connect together, the network help us do this. It works like a network in computer

`Volumes:` A volumne allow us define a workspace to store and interact data between host and docker container

## `II> Syntax basic`
- Check version: ```docker version```
- List image/container: ```docker image/container ls```
- List all existed container: ```docker ps –a```
- Create a container which run below: ```$ docker run -d <name of image>```
- Run container from image: ```$ docker run –name <name of container> <name of image>```
- Start a container: ```$ docker start <name of container>```
- Stop container: ```docker stop <name of container>```
- Stop all container: ```docker stop $(docker ps –a –q)```
- Delete image/container: ```docker image/container rm <name of image/container >```
- Delete all image: ```docker image rm $(docker images –a –q)```
- Delete all existed container: ```$ docker rm $(docker ps –a –q)```
- Show log a container: ```docker logs <name of container>```
- Build image from container: ```$ docker build -t <name of container>```
- Pull image: ```$ docker pull <name of image>```

## `III> Dockerfile`
Dockerfile is a config file which has directives for docker knows how to build a image from a basic image 

### `3.1. Directives`

The directives includes:
- `FROM`: define the root/basic image 

```
EX:
FROM python:3
```
- `LABEL`: provide metadata for image
```
EX:
LABEL version="1.0"
LABEL description="This text illustrates \
that label-values can span multiple lines."
```
- `ENV`: set environment variable
```
EX:
ENV MY_NAME="John Doe"
```
- `RUN`: execute any commands in a new layer on top of the current image and commit the results
```
EX:
RUN ["/bin/bash", "-c", "echo hello"]
```
- `COPY`:  copies new files or directories from `src` and adds them to the filesystem of the container at the path `dest`
```
EX:
COPY hom* /mydir/
```
- `ADD`: copies new files or directories from `src` and adds them to the filesystem of the container at the path `dest`
```
EX:
ADD hom* /mydir/
```
- `CMD`: provide defaults for an executing container. These defaults can include an executable, or they can omit the executable, in which case you must specify an `ENTRYPOINT` instruction as well.
```
EX:
CMD echo "This is a test." | wc -
```
- `WORKDIR`: Define workspace for other directives
```
EX:
WORKDIR /path/to/workdir
```
- `ARG`: defines a variable that users can pass at build-time to the builder with the docker build command using the `--build-arg <varname>=<value>` flag
```
EX:
ARG buildno
ARG user1=someuser
```
- `ENTRYPOINT`:  allows you to configure a container that will run as an executable.
```
EX:
ENTRYPOINT ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
```
- `EXPOSE`: Define port for image
```
EX:
EXPOSE 80/tcp
EXPOSE 80/udp
```
- `VOLUME`: creates a mount point with the specified name and marks it as holding externally mounted volumes from native host or other containers
```
EX:
VOLUME /myvolume
```

### `3.2. How to use`
- Systax to run Dockerfile: `docker build [OPTIONS] PATH | URL | -`
If Dockerfile locate at current path we will use option `-t` instead of ` PATH | URL `
- EX: `docker build -t demoapp:latest`