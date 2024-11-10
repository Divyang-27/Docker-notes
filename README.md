# Docker-notes
Docker commands
Here's a structured guide based on the command history provided. This documentation explains each command with context and steps for setting up Docker, pulling images, managing containers, and working with Dockerized applications.

---

## Docker Setup and Basic Commands

1. **Check Docker Installation and Clear Screen**:
   ```bash
   clear            # Clears the terminal screen
   whoami           # Checks the current logged-in user
   ls               # Lists files and directories
   docker           # Checks Docker installation by displaying available Docker commands
   docker login     # Logs into Docker Hub or another registry
   ```

2. **Docker Image Management**:
   ```bash
   docker pull hello-world    # Downloads the 'hello-world' Docker image
   docker images              # Lists all Docker images on the system
   docker run hello-world     # Runs the 'hello-world' container to verify Docker functionality
   docker rmi hello-world     # Removes the 'hello-world' image
   ```

3. **Container Management**:
   ```bash
   docker ps               # Lists all running containers
   docker stop <container> # Stops the specified container by container ID or name
   docker rmi -f <image>   # Forcibly removes the specified Docker image
   ```

4. **Install and Configure Docker (if not installed)**:
   ```bash
   sudo apt-get update                 # Updates package information
   sudo apt-get install docker.io      # Installs Docker
   sudo systemctl status docker        # Checks Docker service status
   sudo usermod -aG docker $USER       # Adds the current user to the Docker group for Docker permissions
   newgrp docker                       # Refreshes group permissions for the current session
   ```

## Working with MySQL in Docker

1. **Pull and Run MySQL**:
   ```bash
   docker pull mysql                   # Downloads the MySQL image
   docker run -e MYSQL_ROOT_PASSWORD=root mysql # Runs a MySQL container with the root password set as 'root'
   ```

2. **Run MySQL in Detached Mode**:
   ```bash
   docker run -d -e MYSQL_ROOT_PASSWORD=root mysql # Runs MySQL in detached mode (background)
   ```

3. **Connect to MySQL Container**:
   ```bash
   docker exec -it <container_id> bash # Enters a running MySQL container's bash shell for direct interaction
   ```

## Project Setup with Docker

1. **Setting Up a Java Project**:
   ```bash
   mkdir projects                      # Creates a directory for projects
   cd projects                         # Changes into the 'projects' directory
   git clone https://github.com/LondheShubham153/simple-java-docker.git  # Clones a sample Java project
   cd simple-java-docker               # Enters the project directory
   vim Dockerfile                      # Opens the Dockerfile for editing
   docker build -t java-app .          # Builds a Docker image named 'java-app' from the Dockerfile
   docker run java-app                 # Runs the Java application in a container
   ```

2. **Setting Up a Python Project with Flask**:
   ```bash
   mkdir simple-python-project         # Creates a directory for the Python project
   cd simple-python-project            # Enters the Python project directory
   git clone https://github.com/LondheShubham153/flask-app-ecs.git  # Clones a Flask app
   cd flask-app-ecs                    # Enters the Flask project directory
   vim Dockerfile                      # Opens the Dockerfile for editing or creation
   docker build -t flask-app .         # Builds the Flask application Docker image
   docker run -p 80:80 flask-app       # Runs the Flask app and maps it to port 80 on the host
   ```

3. **Running Flask in Detached Mode**:
   ```bash
   docker run -d -p 80:80 flask-app    # Runs the Flask application in detached mode on port 80
   ```

4. **Viewing Docker Logs**:
   ```bash
   docker logs <container_id>          # Retrieves logs for the specified container
   ```

---

## Troubleshooting and Maintenance

1. **Restarting Docker Commands for Errors**:
   ```bash
   docker build -t flask-app .         # Ensures the Docker image builds correctly by specifying the context
   docker ps                           # Lists running containers to check for active processes
   ```

2. **Stopping and Removing Containers and Images**:
   ```bash
   docker stop <container_id>          # Stops a running container by its ID
   docker rmi -f <image_name>          # Force-removes a specified Docker image
   ```

---

### Notes
- **Container IDs**: Replace `<container_id>` with the actual container ID from `docker ps`.
- **Docker Permissions**: After adding the user to the Docker group, restart the session or run `newgrp docker` to refresh permissions.
- **Port Mapping**: Ensure host ports (like 80) are not in use when binding a container to them.
