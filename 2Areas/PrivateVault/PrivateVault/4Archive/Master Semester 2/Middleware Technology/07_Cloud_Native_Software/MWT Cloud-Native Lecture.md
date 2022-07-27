[[0_Intro-Cloud-2-v.1.1.1.pdf]]
# Cloud native
Breaks away from traditional software development of monolith software and focuses instead on creating applications that leverage cloud environments. 

Cloud-native technologies allow orgas to build and run scalable application in modern dynamic environments such as public, private and hybrid cloud. 
Container, microservices and declarative APIs exemplify this approach.

https://docs.microsoft.com/en-us/dotnet/architecture/cloud-native/definition


# CAP Theorem
**C**onsistency - **A**vailability - **P**artition tolerance

Choice between consistency and availability. 

*Availability*
Every request received by a non-failing node in the system must result in a response. 

*Partition tolerance*
The network will be allowed to lose arbitrary many messages sent from one node to another.

# Conway's Law
![[01PrinciplesSummary#Conway's Law]]

# (Domain-Driven Design) 
![[05DDDSummary#Important Terms]]



# 12-factor app 
### Codebase
 One codebase tracked in revision control, many deploys. 

### Dependencies 
Explicitly declare and isolate dependencies. 
- Don't rely on implicit existence of system-wide packages
- Easier for newcomers

### Configuration
Store config in the environment
- Separate config from code (Config varies substantially across deploys, code does not)
- No configuration should be stored in the code -> does not scale
- Store config data in env vars

### Backing services
Treat backing services as attached resources. Which indicates their loos coupling to the deploy they are attached to. 

- Resources can be attached an detached to deploys at will

A backing service is any service the app consumes over the network as part of its normal operation. Eg. DB.

### Build, release, run 
Strictly separate built and run stages. 

### Processes 
Execute the app as one or more stateless processes. 
- Processes are stateless and share nothing. Any data that needs to persist must be stored in a stateful backing service (db). 

### Port binding
Export services via port binding.
- App is completely self-contained and does not rely on runtime injection of a webserver into the execution environment. 
- Exports HTTP as a service by binding to a port and listening to requests coming into that port. 

### Concurrency
Scale out via process model. 
- Processes are first class citizen

### Disposability 
Maximize robustness with fast startup and graceful shutdown. 

### Dev/Prod Parity
Keep development, staging and production as similar as possible. 
- App should be designed for CD by keeping he gap between development and production small 

Time gap, personnel gap and tools gap possible.

#### Logs 
treat logs as event streams. 

####  Admin processes 
Run admin tasks as one-off processes. 

# Microservices

Monolithic (tight coupling) -> Service-Oriented Architecture (looser)-> Microservices (decoupled)

## Why Microservices
- Cap Theorem: Scale out 
- Conway's Law: Two Pizza Teams
- Cloud Service Models (Iass, PaaS, SaaS)
- Containers

### Characteristics
- Single Responsibility
- Share nothing 
- Independent deployable
- Small in Size 
- Resilient
- Complete
- Monitored
- Isolated
- Replicated Data
- Own your state exclusively
- Decoupled in time and space 
- Smart Endpoints, Dumb Pipes 
- Do One thing and Do It Well (Unix Philosophy)
- Decentralized Data Management
- Easily replacable
- Organized around Capabilities 
- Plyglot Development
- Elastic (desposable, fast startup)
- Mandatory infrastrucutre automation
- clusterable 
- scalable
- Act autonomously 

# Serverless and FaaS

## Objective and Exercises
- The student knows about the evolution of distributed systems (and middleware) and the drivers towards state-of-the-art implementation and deployment.
- She/he can explain the underlying concepts and theories and put it into practical context.
- No dedicated exercises for this module. 
- Recap of basics: Spring Boot, Docker, configuration, persistence and messaging._

### Review questions
- "WHY" Cloud-Native Software? What IS Cloud-Native Software?
- Why "evolution" from a monolithic approach to a distributed approach?
- How does the CAP Theorem/Conway’s Law relate to this?
- (NO Domain-Driven Design questions)
- How do the 12-factor application "methodology" relate to the technologies that we covered in this semester? (important)
