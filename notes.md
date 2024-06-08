- When we EXPOSE the port, and run the local to with that port, it not working because the container is run seperate from our computer. we need to map it `docker run -p 5173(container):5173(our machine) react-docker`.

 - When we do some changes to the code, the docker container won't changes anything. To mount the current working directory to the container we need to run this command 
 ```bash
docker run -p 5173:5173 -v "$(pwd):/app" -v /app/node_modules react-docker
```
- The command you provided is used to run a Docker container with specific configurations. Let's break down each part of the command to understand what it does:

1. **`docker run`**:
   - This is the Docker command to run a new container.

2. **`-p 5173:5173`**:
   - This option maps port 5173 on your host machine to port 5173 on the container. This means that if your application inside the container listens on port 5173, you can access it from your host machine on the same port.

3. **`-v "$(pwd):/app"`**:
   - This option mounts the current working directory (the directory from which you run the Docker command) to the `/app` directory inside the container. 
   - `$(pwd)` is a shell command that returns the current working directory path.
   - This allows you to share files between your host and the container, making it easy to develop and test your application.

4. **`-v /app/node_modules`**:
   - This option creates an anonymous volume for the `/app/node_modules` directory inside the container.
   - This is typically done to avoid conflicts between the node modules installed on your host machine and those inside the container. By creating an anonymous volume, you ensure that the node modules inside the container are isolated from those on your host.

5. **`react-docker`**:
   - This is the name of the Docker image you are running. The image should be pre-built and available either locally or in a Docker registry.
   - The `react-docker` image presumably contains your React application and all its dependencies.


- Docker achitecture is?

- Docker is platform for building, running and shipping your application. 
 - missing files.
 - Software version
 with docker we can package everything into a container.

- They say that Docker help other like you have to install the container and it all work just fine, without setting up the environment. But isn't it just see the application work but the other developer skill need to install those envinronment to eb able to run and modify the code right?
   - The devleoper can pull the image and have the same env and code from like the other, they can modify and push normally. Developers can mount their local source code into the Docker container for real-time development and testing.

- Docker use an client-server achitecture 

server is also call Docker Engine

- when we create an image, we can push it to Registry which is like github, so the other can see our image and pull it to use.

- Dovckerfiles Consistency:
   - The `Dockerfile` ensures that everyone is using the same versions of the dependencies, configureations, and environment settings, This eliminates discrepancoes caused by different local setups.


# *Run `docker-compose build --no-cache` sometime there is a cache that make something wrong with the new build*


 - Compose watch can:
   - sync: sync from the host file system to the conatianer file system, to make sure that the code is up to date. 
   - rebuild: rebuild/restart the container.
   - sync restart: sync + rebuild.