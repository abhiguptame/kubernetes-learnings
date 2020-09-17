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
>
> Kubernetes is an open source project that enables software teams of all sizes, from small startup to a Fortune 100 company, to automate deploying, scaling, and managing applications on a group or cluster of server machines.

### Multi-Host Container Scheduling:
- Done by kube-schedular
- Assign pods to nodes at runtime
- Checks resources, qulality of service, policies, and user specifications before scheduling

### Scalability and Availability:
- Kubernetes master can be deployed in a highly available configuration
- Multi-region deployments available

#### Scalability (v1.17)
- Supports 5000 node clusters
- 150000 total pods
- Maximum of 100 pods per node
- Pods can be horizontally scaled via API

### Flexibility and Modularizations:
- Plug-and-play architecture
- Extend architecture when needed
- Add-ons: network drivers, service discovery, container runtime, visualization, and command

### Registration:
- Seamless nodes register themselves with master.

### Service Discovery:
- Automatic detection of services and endpoints via DNS or environment variables.

### Persistent Storage:
- Much requested and important feature when working with containers
- Pods can use persistent volumes to store data
- Data retained across pod restarts and crashes

### Application Upgrades and Downgrades:
- Upgrades: rolling updates supported
- Downgrades: rollbacks are supported

### Maintenance:
- Features are backward compatible
- APIs are versioned
- Turn off/on host during maintainance (unschedulable)

### Logging and Monitoring:
- Application monitoring built-in: TCP, HTTP or container execution healt check 
- Node health check: Failures monitor by node controller
- Kubernetes status: Add-ons (Heapster and cAdvisor)
- Logging framework: In place or extensible

### Secrets Management:
- Mounted as data volumes or environment variables
- Specific or namespace

## Major Players in Container Orchestration:
- Kubernetes
- Docker Swarm
- Rancher
- Mesos

### Cloud-specific Technologies:
- Amazon EC2 Container Service
- Google Anthos

## When to go serverless:
- Starting to build our infrastructure from scratch 
- Running our infrastructure in cloud

## Basic building blocks: Nodes and pods

### Node:
- The node serves as worker machine in a K8s cluster. One important thing to note is that the node can be a physical computer or a virtual machine.

#### Node Requirements:
1. A kubelet running
2. Container tooling like Docker
3. A kube-proxy process running
4. Supervisord

> * Recommendation:
>
> If we are using Kubernetes in production, it is typically recommended to have at least a three-node cluster.

#### Minikube:
- Lightweight Kubernetes implementation that creates a VM on our local machine and deploys a simple cluster containing only one node.

### Pod:
- The simplest unit that we can intract with. We can create, deploy, and delete pods, and it represents one running process on our cluster.

#### What's in the Pod?
- Our Docker application container
- Storage resources
- Unique network IP
- Options that govern how the container(s) should run

#### Pods are:
- Ephemeral, disposable
- Never self-heal, and not restarted by the schedular by itself
- Never create pods just by themselves
- Always use higher-level constructs.

#### Pod States:
- Pending
- Running
- Succeeded
- Failed
-  CrashLoopBackOff

## Benefit of Controllers:
- Application reliability
- Scaling
- Load balancing

## Kinds of Controllers:
- ReplicaSets
- Deployments
- DaemonSets
- Jobs
- Services

### ReplicaSets:
- Ensures that a specified number of replicas for a pod are running at all times.

### Deployments:
- A Deployment controller provides declarative updates for pods and ReplicaSets.

#### Deployment Controller Use Cases:
- Pod management: Running a ReplicaSets allows us to deploy a number of pods, and check their status as a single unit.
- Scaling a ReplicaSet scalesout the pods, and alllows for the deployment to handle more traffic.
- Pause and Resume: 
1. Used with larger changesets
2. Pause deployment, make changes, resume deployment
- Status
- Easy way to check the health of pods, and identify issues

#### Replication Controller:
- Early implementation of Deployments and ReplicaSets.
- Use Deployments and ReplicaSets instead.

### DeamonSets:
- DaemonSets ensure that all nodes run a copy of a specific pod.
- As nodes are added or removed from cluster, a DaemonSet will add or remove the required pods.

### Jobs:
- Supervisor process for pods carrying out batch jobs.
- Run individual processes that run once and complete successfully.

### Services:
- Allow the communication between one set of deployments with another
- Use a service to get pods in two deployments to talk to each other.

#### Kinds of Services:
- Internal: IP is only reachable within the cluster
- External: endpoint available through node ip: port (called NodePort)
- Load balancer: Exposes application to the internet with a load balancer (available with a cloud provider)

## Labels, selectors, and namespaces:

### Labels:
- Labels are key/value pairs that are attached to objects like pods, services, and deployments.
- Labels are for users of Kubernetes to identify attributes for objects.
> Think about what our environment look like, and create a labeling hierarchy for it.

#### Labels and Selectors:
- Label selectors allow us to identify a set of objects.

### Selectors:
1. Equality-based
2. Set-based

#### Equality-based Selectors:
- *=* , Two labels or values of labels should be equal
- *!=*,  The values of the labels should not be equal

#### Set-based Selectors:
- IN: A value should be inside a set of defined values
- NOTIN: A value should not be in a set of defined values
- EXISTS: Determines whether a label exists or not

### Namespaces:
- Great for a large enterprises
- Allows teams to access resources, with accountability
- Great way to divide cluster resources between users
- Provides scope for names-must be unique in the namespace
- "Default" namespace created when we launch Kubernetes
- Objects placed in "default" namespace at start
- Newer applications install their resources in a different namespace

## Kubelet and kube-proxy:

### Kubelet:
- The Kubelet is the "Kubernetes node agent" that runs on each node

#### Kubelet Roles:
- Communication with API server to see if pods have been assigned to nodes
- Executes pod containers via a container engine
- Mounts and rund pod volumes and secrets
- Executes health checks to identify pod/node status

#### Kubelet and Podspec:
- Podspec: YAML file that descibes a pod
- The kubelet takes a set of Podspecs that are provided by the kube-apiserver and ensures that the containers described in those Podspecs are running and healthy
- Kubelet only manages containers that were created by the API server, not any container running on the node

### kube-proxy:  The Network Proxy
- Process that runs on all worker nodes
- Reflects services as defined on each node, and can do simple network stram or round-robin forwarding across a set of backends
- Service cluster IPs and ports are currently found through Docker --link compatible environment variables specifying port opened by the service proxy.

#### Three Models of kube-proxy:
1. User space mode
2. Iptables mode
3. Ipvs mode (alpha feature)

#### Why These Models Are Important:
- Services defined against the API server: kube-proxy watches the API server for the addition and removal of services
- For each new service, kube-proxy opens a randomly chosen port on the local node
- Connections made to the chosen port are proxied to one of the corresponding back-end pods







