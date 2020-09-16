# Kubernetes Learnings:

## What is containerization?

### Container:
- A collection of software processes unified by one namespace, with access to an operating system kernel that it shares with other containers and little to no access betweeen containers.

## Docker Instance:
- A runtime instance of a Docker image contains three things:
1. A Docker image
2. An execution environment
3. A standard set of instructions

## Docker Engine:
- Comprised of the runtime and packaging tool 
- Must be installed that run Docker

## Docker Store:
- An online cloud service where users can store and share their Docker images
- Also known as Docker Hub

## Virtual Machine (VM):
- One of many applications
- The necessary binaries and libraries
- The entire guest operating system to interact with the applications

## Containers:
- Include the application and all of its dependencies
- Share the kernal with other containers
- Not tied to infrastructures only needs Docker Engine installed on the host
- Run as isolated processes in user space on the host OS

## Container Benefits for Developers:
- Automated testing, packaging, and integration 
- Support newer microservice architecture
- Alleviate platform compatibility issues


### Applications are:
1. Portable 
2. Packaged in a standard way

### Deployment is:
1. Easy
2. Repeatable

## Container Benefits for DevOps:
- Reliable deployments: improve speed and frequency of releases
- Consistent application lifecycle: configure once and run multiple times
- Consistent environment: No more process difference betweeen dev and production environments
- Simple scaling: Fast deployments ease the addition of workers and permit workload to grow and shrink for on-demand use cases















