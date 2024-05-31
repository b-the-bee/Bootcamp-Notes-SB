#data-engineering #data-science #docker

## Overview
- A brief history of software deliverry
- An Introduction to docker

- Commands to work with Docker containers
- Creating your own Docker containers
- Sharing your containers with the world


## Learning Objectives
- Explain the benefits of images and containers
- Use commands to start, stop and log into containers

- Understand the structure of a Dockerfile and be able to write one
- Demonstrate how Docker Compose can create and run multi-container applications


## The history of Software Delivery

### Multitasking operating systems
Install many programs to disk and run them on demand

![[Pasted image 20240529133850.png]]

### Virtualisation
Can isolate dependencies in individual VMs

![[Pasted image 20240529133946.png]]

### Containerisation (Docker)

Docker is a tool designed to make it easier to create, deploy and run applications by using **containers**.

Containers allow a developer to package up an application with all of the parts it needs, such as libraries and other dependencies and ship it all out as one package.

![[Pasted image 20240529134130.png]]

![[Pasted image 20240529134227.png]]

![[Pasted image 20240529140222.png]]
![[Pasted image 20240529140507.png]]

![[Pasted image 20240529140529.png]]

![[Pasted image 20240529140548.png]]

![[Pasted image 20240529140617.png]]
## Removing and restarting
- `docker rm <id>` - remove a container 
- `docker restart <id>` - restart a container

![[Pasted image 20240529143926.png]]
![[Pasted image 20240529144428.png]]![[Pasted image 20240529152109.png]]


![[Pasted image 20240529153931.png]]![[Pasted image 20240529161828.png]]