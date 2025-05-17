References:
[NetworkChuck - Docker 101](https://youtu.be/eGz9DS-aIeY?si=4UnT3paqOS0X7-aJ)
[The Coding Sloth - Docker](https://youtu.be/DQdB7wFEygo?si=s8V0gmA-gUBAvk-O)
[Better Stack - Docker Image Best Practice](https://youtu.be/t779DVjCKCs?si=JptsauE4d7dL7i_S)
[Dave's Garage - Docker]([https://youtu.be/0gCRw13C2Xw](https://youtu.be/0gCRw13C2Xw "Share link"))
[Dzone article](https://dzone.com/articles/how-do-the-docker-client-and-docker-serves-work)
[Coderized - Docker](https://youtu.be/J0NuOlA2xDc?si=eohJMDyYaEAFSODc)
# What is Docker?
A Container Platform $\rightarrow$ A tool that helps you develop, ship, and run applications within light-weight container $\rightarrow$ make development and deployment easier $\rightarrow$ enable you to package your code (code, code dependencies, environment setting etc.)
Docker most concepts $\rightarrow$ images + containers
* Container Platforms: Podman, Docker, LXD
## VM vs Container
Containers are Faster and less resource intensive. 
![[Difference-Between-VM-VE-Container]]
### Virtual Machine 
Our whole hardware could be only be used by only one OS (operating system) $\rightarrow$ Virtual Machine: instead of installing one OS we install one Hypervisor $\rightarrow$ divide your resource into multiple servers; VMware, ESXI
### Docker
One OS on your whole hardware (old approach)
* With VM you virtualize the Hardware
* With Docker you virtualize the OS
Docker provide a platform for shipping, developing and running applications on Containers, While [[Kubernetes]] offers a orchestration system for automating the deployment, scaling and management of Containerized Applications.
**Problem:**
you can only install linux container on a linux base system, and you can only create windows container on a windows base system, because they share the same underline OS
**Pros:**
Micro-service, have multiple compatible services in different location and when you want to update one, you just update part of your system
# How to install Docker?
by just simply download docker desktop $\rightarrow$ it comes with Docker.exe (client side/CLI) + Dockerd.exe (docker daemon/docker engine) $\rightarrow$ in background these 2 components talk to each other through the REST API $\rightarrow$ every command executed by the client will be translated by the REST API and then talk to server (docker daemon) and then sent out the process by the daemon
![[Docker-Workflow]]
* docker CLI `docker --hlep`
* you can check if you have docker installed by simply do `docker --version`
* in unix system we call background processors daemon
# Docker Components
## Images
something like recipe, contains:
* Technologies we need
* Runtimes Environment (Application code, libraries, dependencies, configurations)
* The tools/instructions to run our code
result into guarantee compatibility and reduce conflicts
### Pull image 
```
docker pull name_of_the_image
```
download images from docker hub
## Dockerfile
Build your own image 
```
# Uses node version 22 as our base image
# Every Dockerfile start with this
# 22 is our tag for that image
FROM node:22 

# Goes to the app directory
WORKING /app

# Copy package.json and package-lock.json (if available)
COPY package*.json ./

# Install app dependencies
RUN npm install 

# Set port environment variable 
ENV PORT=9000

# Expose the port so our computer can access it
EXPOSE 9000

# Run the app
CMD ["npm", "start"]
```
Why we are doing this? Layer Caching
* What is the difference between `RUN` and `CMD`? `RUN` is for the time that you are building the image, `CMD` to start the container after building
	* You only have One `CMD` command
### Build the image
build your container from your Dockerfile
```
docker build -t(tag, give a name to your contianer) name_of_the_contianer path_to_Dockerfile
```
### Optimize your image
#### Minimal Base Image
> [!Warning] It can cause compatibility issues
> if you using native libraries, the probability of causing the problem will increase

Alpine;
* Purposely built for containers
* Linux in its bare minimum version to only run the apps
* Most used thing will probably have this minimal version

> [!tip] Use the full image for your development container, find the best minimal version for your production
> very optimized version [Distroless Container Images](https://github.com/GoogleContainerTools/distroless)
#### Layer Caching
* it is like Version Control but for images
instead of changing data at it's source, file changes are track by differences from a previous layer and in the End compose together and make Image.
every step is a layer and docker looks at every layer individually:
layer change = do it again (rebuilt it)
layer did not change = use cache
* if one layer changes all layers that come after will have to be rebuilt too
	* every time you change your code it will not download dependencies again, it will use the cache
##### Cache Invalidation Causes
* Changes to the files you're copying
* Changes to the Dockerfile instruction
* Changes to any previous layer

> [!tip] Order Matters! Dockerfile
> Have low frequent change at top, Have high frequent change at bottom
##### Layer Squashing
* Each layer in Docker is immutable and container only changes from the previous layer $\xrightarrow{so}$ Separate RUN commands create new layers, preserving files from earlier layers $\xrightarrow{so}$ Deleting files in later layers don't remove them from earlier layers $\xrightarrow{so}$ Deleted files are marked as 'not accessible' but still consumer space in the image $\xrightarrow{so}$ Docker can't remove data from previous layers due to their immutability $\xrightarrow{so}$ instead of multiple run commands use Single Run command
#### Docker Ignore
`.dockerignore` to lower the transferring context (docker build) by ignoring the un-need files (like .gitignore)
#### Multi-Stage Builds
instead of doing things in one go, break it into smaller pieces
* Each `FROM` will create a new stage
	* you still have one Dockerfile with multiple `FROM` in it
* Nothing is carried over to the next stage unless you specify them
## Container
A place to run your code
A place created from your Images, you can have multiple container created from same image $\xrightarrow{why}$ because when a container created from an image, the image file system will extend with new file system layer completely dedicated to that container
Crazy fast, light weight, micro computers
Key features: Isolation + Portability + Platform independent + Efficiency + Security
* **Isolation:**
ability to provide Isolation through technologies **namespaces** and **control-groups** separate apps and the host from each other
	 **namespaces**: give distinct view for each container on its resources; process id, network interface, file systems
	 **control-groups**: limit and monitor the resource of each container can use; cpu, memory, disc IO
* **Portability:**
	packaging the application and dependencies together $\rightarrow$ application will run across different environments
* **Platform Independent:**
	Cloud Or Laptop
* **Efficiency:**
	Share the Kernel of the Host
* **Security:**
	use features like Secure Computing mode (seccomp)
### Create & Run
```
docker run -d -t --name name_of_the_image
```
check what container is running
```
docker ps
```
list my docker containers
```
docker container ls
```
#### Debugging in Docker
connect to my container
```
docker exec -it name_of_the_container bash
```
type `exit` to exit
#### Port Forwarding
A network configuration technique that allows external devices to access services on a private network
Bridge between computer and container
```
docerk run -p 8080:80 name_of_the_image
-p Computer Port:Container Port
```
result will show localhost:8080
#### Tag
Give you ability to download different version of a image
```
docker pull image:tag
```
how to run a docker image with tag
```
docker -t -d -p 80:80 --name name_of_the_container image:tag
```
how to stop my containers?
```
docker stop name_of_container
```
start them again
```
docker start name_of_container
```
##### Flags
`-it` running containers interactively, getting access to container output
`-rm` delete any existing copy of a container and start fresh
`-d` detached, process will be run in the background
`-p` map container port to host
#### Resource Usage
see how much resource each container use
```
docker stats
```
ctrl+\ to quit the stat
#### Docker Scout
to check the vulnerability of an image
```
docker scout quickview
```
## Docker Compose
instead of having one giant container that combine database, front-end, back-end instead we separate them $\rightarrow$ Multi Container Application $\xrightarrow{problem}$ Run all these containers + how to connect them to each other $\xrightarrow{solution}$ Docker Compose Tool: tell all containers how to work together
### Compose.yml
```
services:
  backend:
    build: .
    ports:
      - '9000:9000'

  db:
    image: postgres:latest
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: pass
      POSTGRES_DB: mydb
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```
## Docker Volume
when you stop running a container you lose all the data states and we don't share that data to other container $\xrightarrow{solution}$ Docker Volume: folder on our computer/vm which docker can access to; save data from our containers + share that data to other containers.
```
docker compose up
```
## Docker init
docker will create everything for you :D
like a git init
```
docker init
```

## Tools
* [Dive](https://github.com/wagoodman/dive)
* [Slim](https://github.com/slimtoolkit/slim)
