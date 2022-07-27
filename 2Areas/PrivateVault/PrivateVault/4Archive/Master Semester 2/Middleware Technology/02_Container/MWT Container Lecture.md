[[2_Containers-and-Docker-v.1.1.1.pdf]]
#docker #container | #lecture #master

# What are Containers? 
- Isolated environment for an application 
- containing all necessary deps, libs, binaries and configs needed. 

## Technical words 
- A container is a **linux process** or many processes 
- running isolated from other processes on the system 
- using **chroot system call** 
	- changes the root dir of a process and its children to a new location 
- and some **linux kernel features** as **cgroups** and **namespaces**
	- namespace wraps system objects in an abstraction that limits the visibility an object has on other objects. 
		- Container processes are limited to see only what is in the same namespace. 
	- cgroup (Control group) limits the usage of resources for a group of processes or containers. 

# Why do Containers exist?
Solution to the problem how to get software to run reliably when moved from one computing env to another. 

- Abstraction 
- Isolation
- Portability 
- Security 
- Agility 
- Disposability 
- Scalability.

DevOps

# Container vs. VMs
**Hypervisors** create an OS based on an image on an existing bare metal machine. 

**Containers** reuse existing OSs configs and libs.

## Containers 
- Virtualize the required file system 
- Use/share the kernel of the host 
- Lightweight 
- Near native performance 
- Booted up in seconds
- Lower amount of storage 

## VMs
- Virtualize a complete OS
- Virtualize kernel of the hist 
- Heavyweight 
- Performance overhead as machine instructions are translated from guest to host os 
- Take mins to boot up 
- Take more storage because whole OS kernel and programs have to be installed and run. 

# Technologies that let to the evolution of Docker
- Which technologies led to the evolution of docker (and why)? VMs, namespaces, chroot, cgroups, LXC, CF/Google containers

[[History of Docker]]

*Chroot* war the first linux kernel feature which made is possible to provide isolation for linux processes.

**LXC** was the first complete container manager. 

*cgroups* with which is it is possible to limit resources for a group of processes or containers.  

*namesspaces* where introduced which allowed that one set of processes is able to see resources that arent't visible for other processes.

# Docker 
## Components 
- Docker-Daemon 
- Docker Hub
- REST API
- Docker-Client 

**Docker hub** is a cloud registry service that enables storing and discovery of Docker images and automating workflows. 
Provides public and private repos 

**Docker daemon** is a persistent background process that manages docker images, containers, netwroks and storage volumes. 
Constantly listens for Docker API requests and processes them. (the docker d command )

**REST API** An API used by apps to interact with the Docker daemon. It can be accesses by an HTTP client. 

**Docker-Client** A CLI for interacting with docker (the docker command)


### What is the difference between docker daemon and docker hub?

## Build your own Docker Container 
1. Write a Dockerfile 
2. Build a Docker image of your app
	- *docker built*
1. Run your Docker container (app) locally 
2. Push Docker image into a registry if needed 

Other options (next to dockerfile)
- Jib, Palketo, Cloud native Buildapck

### Essential Docker Commands 

### Command on docker image 
*docker commit*
Turns current state of container into image. 

*docker tag*
Set name for docker image. 

### Commands on container
*docker start/stop/restart/kill*
Perform the corresponding actions on an container

*docker run*
Creates container of specified image and then starts it. `Create` and `start` in one. 

*docker inspect*

*docker logs*

### Docker hub
*docker pull*
Pulls an image or an repos from a registry. 

*docker push*
Pushes image on docker hub or other ext. registry.


`docker exec <options> <container> <command>` i
**Example** 
```bash
docker exec 74f11111 ls 
```

# Internals of an image 
- Images are structured in layers -> Not everything has to be stored in on piece. Docker can operate more efficient. 

## Dockerfile
*FROM* Base Image 
*CMD* Default commands when image is instantiated 
*WORKDIR* Set working dir for all consecutive commands
*ENV* Sets the evn variables fro subsequent instructions
*COPY* Copy files or dirs from source to host filesystem
*LABEL* Add metadata to the image
*RUN* Executes the instructions in a new layer on top of the existing image and commit this layers and the resulted layer will be used for the next instructions in the Dockerfile.
*ADD* Add files or dies from host file system to destination in the container file system.
*ARG* Pass arguments to consecutive instructions.
*EXPOSE* Documentation for port
*USER* Sets user name when running image and instructions in Dockerifle.

# Not so relevant 

## Contianer vs. Container Images 
### Container 
- Begin lifecycle using an image 
- Running instance of an image 
- Many container can be run off the same image 

### Container Image 
- Never stared, never running 
- Blueprint of a container 
- Ensure reusability of containers 




## System Containers vs. Appl Containers 
## Application Container 
- Runs a single app 
- Built on top of system container

## System Container
- Runs an OS 
- The entry point is an init system 
-Builtt on cgroups, namespaces and native processresourcee isolation.


# Learning 
## Objectives 
Student understands 
- concepts and use cases of container technology and can descrive the
- pull example images from the an image registry and interact with them
- Built custom image via dockerfile and push it to an registry 

## Review questions
- "WHY" Containers? List advantages/disadvantages ..
- What is the difference between a container and a VM? List 3 criteria
- Which technologies led to the evolution of docker (and why)? VMs, namespaces, chroot, cgroups, LXC, CF/Google containers
- What is the difference between a docker daemon and the docker hub? Daemon = runtime, Docker Hub = public registry
- What is the difference between docker run, docker pull and docker start?
- Which command transitions from a container instance to an image?
- What are the Docker components and describe them?
- What does docker exec do? Provide a pseudo-code example and explain what it does