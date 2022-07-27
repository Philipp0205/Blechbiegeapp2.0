

# Configuration 
## Why 
Any time spent writing config is time spent not writing application logic. 

## External config by file 
- Can be injected through property file 
- Possible with `@PropertySource` or `@Value`. 
- Use of environment variables or maven properties or java properties possible as well. 
	- These variables  can be overwritten. Environemnt variables will always overwrite things in the properties. 
	- If Spring as mulitple entries for the same value one will win over the other one. 

## Profile
- User different applicatoin properites and summarize these in a profile and then you can activate different profiles during runtime. 

## Limitations of local properties 

## Config Server
- Server sided option for configuration 
- It's a own microservice 
- Possible to hold many configs for many microserveices on one place 
- config updatable while app is running 
- Can be encrypted 
- Does not need to be stored in the local repo 
- On the other side the applications needs that server and won't work without it 
- config serer is a spring boot app which exposes props with REST Api 


![[Pasted image 20211203101531.png]]
- Why is the code wrong? 
	- No config in code


