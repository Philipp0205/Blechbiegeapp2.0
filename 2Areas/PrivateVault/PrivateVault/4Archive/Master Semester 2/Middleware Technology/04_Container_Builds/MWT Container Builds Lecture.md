[[JFS_2021_Haeussler_Novatec_Options_Galore.pdf]]
# Container, Images, Layers 
## Image 
- Represents a packaged application with all the dependencies needed to run. 

### Layer 
Are built as a series of **layers**.
- OS layer 

*docker commit*
Creates a new image from a container's changes. 
Basically takes a "snapshot" of the current state of the running container and saves it as an image. 

*docker build* 
Create image from Dockerfile. Creates only new image if it detects changes. 

## Container 
Instance of an image with id. 

![[Pasted image 20220110172502.png]]

To do these steps manually would be very time consuming -> done in *Dockerfile*.

Docker file does all the command between the run and commit commands. 
![[Pasted image 20220124103116.png]]

# History of Dockerfile 
## Multi-Stage Dockerfile 
Dockerfile can be divided into stages 
- For each stage one image will be created 

- Smaller docker images  
- Can just use the built artefact from a previous stage and leave any intermediate artefacts behind -> not saved in the final image. 

- With **cache** id it does not need to download again.

## Buildkit 
- faster builds 
- improved caching
- smaller images 
- parallel and skipped stages 
- flow logic 
- improved security 

# Criteria for good images 
- Speed
- Size 
- Structure 
- Standardisation 

## Using layered jars 
![[Pasted image 20220124112549.png]]

Only the layers which change will be rebuilt -> makes the built faster.  


# Using Jib, Cloud-Native Buildpacks and Paketo

## Adv./Disadv Dockerfile
**Disadvantage**
- Each Dockerfile becomes another piece of code that you -> correctness, efficiency, security. 

**Advantage**
Very flexible, everything can be done manually.

## Jib
- Containerisation for java application. 
- No need for docker daemon. 
- Maven/Gradle plugin 
- More direct way from app to container image
- Faster path from code to container 

## Buildpacks & Paketo
- Goal: Get code quickly into a container and dispose it on the internet. 
- Only one runtime image -> not dev responsiblity, consistency

![[Pasted image 20220111181934.png]]

### Flow 
...

### Objectives and exercises
- The student understands the relation between container image and container, 
- how to instantiate a container from an image and how to commit to a new image from an existing container. 
- The exercise is to build the previous Spring Boot application and put it into a container image using various options, e.g. different Dockerfile optionös, Google JIB, CND, Paketo and more …? 
- The student is aware and able to describe on a high-level what the different fundamentals of the various approaches 
- and is able to list advantages and disadvantages.

# Review Questions 
- List 3 different options to build a container image
- Explain docker build vs docker commit
- List 2 evolution steps of the Dockerfile and provide 1 improvement for each step (multi-stage, buildkit, caching)
- Explain or list 1 advantage&disadvantage comparing JIB and Paketo/CNB to original Dockerfiles
	- **Advantage** 
		- No baseimage and dockerfile needed. Everything will be builded automatically. 
		- Baseimage always stays the same -> more security because in docker bugs could appear in very image. 
	- **Disadvantage**
- How is a container image build up internally? Layers(!) → effective storage of container binaries
- Which are criterias you can think that make image building "better" - less manual steps, less config, smaller size, faster build speed, effective structure

### Possible exam questions 
- What does are things that make a docker build / docker image good? 
- When you pull an image what are the "hashes" in the terminal
	- the layers which are download individually  
