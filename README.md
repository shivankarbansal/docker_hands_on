## Run multiple dependent containers with help of docker compose
```ruby
docker-compose -f docker-compose.yaml up
```
## Stop the containers
Ctrl+c to stop the container
## Remove containers from docker engine
```ruby
docker-compose -f docker-compose.yaml down
```
## Key components of docker-compose.yaml file
- restart:always is useful in case of dependent container eg: mongo-express
is dependent on mongo-db container hence use it so as to avoid docker compose
from crashing
- Volumes is important for persistent data on containers.
- Environment is used for environment variables that is needed to run
image. Ports are default port for that particular microservice
## Python and node js project discussion
Python
## To build container out of image
```ruby
docker build -t <docker_username>/<repo name>:<version><location of Dockerfile which is indicated in the end as .>
```
- **Example**
```ruby
docker build -t shivankarb/containerise-python-hello:0.0.1.RELEASE .
```
## Verify if container is running fine or not
```ruby
docker container run -d -p 3000:3000 shivankarb/containerise-python-hello:0.0.1.RELEASE
```
## Push to dockerhub
```ruby
docker push shivankarb/containerise-python-hello:0.0.1.RELEASE
```
## Key components of Dockerfile
- We use python image as base image from lot of available python images.
- Create directory app and then copy all content of existing folder where this
dockerfile is to app directory
- Install all dependencies
- Expose the port on which we want to run the application. Within python app port
is 3000. We can make it 4000:3000 as well and run our app on 4000.
- Then use python command to execute the app from entrypoint that is index.py
- .(DOT) after RELEASE in build command indicates the location of Dockerfile which
is the current directory
## Node js
Steps very similar to python