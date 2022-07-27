[[Kubernetes_MHS_2021.pdf]]

# How to get to Kubernetes 

Running distributes docker demons
- maintenance of 2 different docker environments 
- docker virtual network bound to one demon 
- own network config and handling 
- **load balancing**
- adding, configuration and handling of an own load balancer
- adding, config and handling of a central service registry
- manual implement of adaptive scaling

![[Pasted image 20211210085208.png]]

"If you re-implemnet that you have **Kubernetes**"

# (History) 
- Google developed borg 
- And then docker was coming to the market 
- Google saw there is a demand for managing and orchestrate containers outside of google. 
- G decided to open source their borg app and called it kubernetes 
	- C++ -> Go 
--- 
- Today kubernetes is part of the cloud native foundation 

## Overview
- Kubernetes coordiantes a highly available cluster of computers that are connected to work as single unit. 
- Provides simplicity of PaaS with flexibility of IaaS
- the abstactions in Kubernetes allow you to deploy containerized apps to ca cluster without tying them to an individual machine. 
---
- Kuberenetes is a **orchestrator**.

## What does Kubernetes do 
- Helps to make containerize apps run where and when you want
- Finds resources and tools they need to work.  


**Example**
- One application can be deployed on two notes. 
- If one of the node fails the orchestrator migrates to the other node automatically. 

## Caas
(Container as a Service)

## CaaS Concepts
- Provides complete container environment for deploying and managing containers, apps and clusters
- Container Orchestration lies at the heart of container platforms 
- Focus on creating the app containers and maintaining them in the future. 


## Dev Reponsiblity 
![[K8Components.svg]]

*Cluster*
Logical unit consists of one *master node* and multiple *worker nodes*.

Consists of two types of resources 
- **Control Plane** coordinates the cluster
	- Obsevers the database deployments and created ReplicaSets if needed and wirtes them in the databases 
- **Nodes** run apps 
	- VM or physical computer
	- Communicate with the control plan using Kubernetes API

*Master node*
Server responsible for the Kubernetes management tasks. 

*Scheduler*
Place the containers on the workers according to various policies.

*Controller manager* 
Will validate and verify if the things on the worker nodes are fine or not .

*API* 
REST interface to all of the Kubernetes resources. 

*Worker node*
Managed by the master components 

*Kubelet* 
Communication with the master services. 

*Kube-proxy*
Managing network connectivity to the containers. 

*Docker Engine*
Container host that creates and runs Docker containers.


## K8s Components 
*Pod*
- Is the smallest unit
- Contains multiple containers 
- Pots get discovered by the scheduler and schedules them to nodes. 
- To run the pod a container image is needed.

*ReplicaSet* 
Specifies how many pods will be run.


### Deployment
Containerizes apps can be deployed on a cluster 

To do so **Deployment config** is needed 
- Instructs Kubernetes how to create and update instance of your app. 

- One app instances are created, a Kubernetes deployment controller continuously monitors those instances
	- if an instance goes down or is deleted replaces the instance with another node in the cluster -> self-healing

### Expose app 
- Pods are mortal and have a lifecycle. 
- When a node dies the pods running in that node are lost -> ReplicaSet fixes that.

Pods an be exposed using a *service*.

A Service is an abstraction which defines a logical set of Pods and a policy by which to access them. 
- Enable a loose coupling between dependent Pods 
- Match a set of Pods using labels 
- Service is defined using YAML.

### Scaling 
Accomplished by changing the number of replicas in a deployments. 

Services have an integrated load-balancer that will distribute network traffic to all pods of an exposed deployment.

#### Scaling Demo Question 
When scaling down the test application failed for some time and the question was why. 

- The service (load balancer in the service) was routing to a pod but the application in the container in the pod was not started yet. 
- Kubernetes does not know what is happening in the containers. It only sees if a container is started or stopped. 

Solution:
- Kubernetes liveness probe -> checks if application in container is ready/alive
- For a Spring App we could use a readiness httpGet Probe and the actuator/health endpoint to see if the app is ready. 

## Advantage of Kubernetes 
- Live updates / patches without downtime 
	- Same for rollbacks
	- -> graceful transition between versions 
- Manual and automatic scaling
- Automatic distribution across nodes
- Automatic load balancing through services
- Automatic restart of failed pod
- Rollout history 
- Dev/Prod parity with namespaces

![[Pasted image 20220126160215.png]]

### Review questions
- Please write 100 lines of YAML Code :)
- Explain the relation of "some" of the 12 factors in relation to Kubernetes
- Explain the core principe of Kubernetes in own words. "Why" Kubernetes?
- What is pod? What is a service?
- Which kind of Kubernetes providers do you know? Can they be grouped somehow? *

- Why do some request fail when we scale kubernetes 
	- when a replicate set (starts) it need time and in that time the requests fail