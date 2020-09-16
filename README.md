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

## Orchestrator Features:
- Provision hosts
- Instantiate containers on a host
- Restart failing containers
- Expose containers as services outside the cluster
- Scale the cluster up or down 

## Kubernetes (K8s):
- Definition: An open-source platform designed to automate deploying, scaling, and operating containers

- Goal: To foster and ecosystem of components and tools that relieve the burden of running applications in public and private clouds

- Kubernetes is a platform to schedule and run containers on clusters of virtual machines. It runs on bare metal, virtual machines, private datacenter and public cloud.

## Kubernetes and Docker:
- Kubernetes is a container platform.
- We can use Docker containers to develop and build applications, and then use kubernetes to run these applications on our infrastructure.

## Kubernetes Features:
> - Joe Beda
> Kubernetes is an open source project that enables software teams of all sizes, from small startup to a Fortune 100 company, to automate deploying, scaling, and managing applications on a group or cluster of server machines.





