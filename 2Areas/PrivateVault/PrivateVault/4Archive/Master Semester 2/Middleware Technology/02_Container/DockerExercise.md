
# Docker most important commands
## List running 
List all running containers
`docker ps`

List all containers (also stopped)
`docker ps -a`
Only display container ids 
`docker ps -q`

## Run containers
Run container normal
`docker run novatec/technologyconsulting-hello-container:v0.1`

Run container detached mode
`docker run -d novatec/technologyconsulting-hello-container:v0.1`

Run container with options

- port maping
	- `docker run -d -p 8080:8080 novatec/technologyconsulting-hello-container:v0.1`
- Environment variables
	- `docker run -d -p 8080:8080 -e PROPERTY=Stuttgart novatec/technologyconsulting-hello-container:v0.1`
- Container name
	- `docker ps -a --format "Id: {{.ID}} Name: {{.Names}}"` 

```bash
docker run --name <name> <image name> 
```



## Clean Up`
Stop all running containers
 `docker ps -q | xargs docker stop`
 
Remove all containers
`docker ps -a -q | xargs docker rm`
 

### Delete image
`docker rmi <image name>`

