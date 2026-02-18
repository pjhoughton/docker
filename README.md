## 🧩 Docker README

```markdown
# Docker

## Overview
This repository contains Dockerfiles and Compose configurations for containerized applications in my homelab.  
It simplifies deployment and ensures consistent environments.

## Vision & Documentation
This repository is part of my broader homelab and automation projects.  
For the full vision, detailed documentation, and cross project context, visit my website:  
👉 [pjhoughton.github.io](https://pjhoughton.github.io)

*Building blocks of my homelab — automation, containers, and smart integrations, shared openly.*

## Getting Started
### Prerequisites
- Docker Engine 24+
- Docker Compose v2

### Usage
Build and run a container:
```bash
docker build -t myapp .
docker run -d -p 8080:80 myapp


Docker and Docker Compose Repository
This repository contains configurations for managing multiple Docker containers using Docker Compose. The setup includes:

A main docker-compose.yml file.

Individual YAML files for each container that extend the main Compose file.


single docker host

ProjectRoot
├── docker-compose.yml          
├── docker-compose.container1.yml  
├── docker-compose.container2.yml
├── README.md
└── .gitignore                

multiple docker hosts 

ProjectRoot
├── services/
│   ├── docker-compose.container1.yml           
│   ├── docker-compose.container2.yml   
│   └── docker-compose.container3.yml   
│
├── stacks/
│   ├── app1/
│   │   ├── docker-compose.yml 
│   │   └── .env                   
│   │
│   └── iotapp1/
│       ├── docker-compose.yml   
│       └── .env                        
│
├── README.md                           
└── .gitignore                     




Usage
Prerequisites
Docker: Ensure Docker is installed on your system. You can install it from Docker's official site.

Docker Compose: Verify Docker Compose is installed. You can check the version by running:

bash
docker-compose --version
Running the Project
Step 1: Pull Images and Start All Services
To start all containers with the main and extended configurations:

bash
docker-compose -f docker-compose.yml -f docker-compose.container1.yml up -d
Use the -f flag to specify additional YAML files for other containers as needed.

Step 2: Check Running Containers
Confirm that all containers are running:

bash
docker ps
Step 3: Stop All Containers
To stop all running containers without removing them:

bash
docker-compose down
Common Commands
Docker Commands
Command	Description
docker build -t <image_name> .	Build an image from a Dockerfile
docker images	List all Docker images
docker ps	List running containers
docker stop <container_id>	Stop a specific container
docker rm <container_id>	Remove a container
docker exec -it <container_id> bash	Access a container's shell
Docker Compose Commands
Command	Description
docker-compose up -d	Start containers in detached mode
docker-compose down	Stop and remove all containers
docker-compose logs -f	Tail logs for all running containers
docker-compose exec <service> <command>	Execute a command inside a running service
Working with Git
Cloning the Repository
To clone this repository, run:

bash
git clone <repository_url>
Common Git Commands
Command	Description
git status	View the status of the repository
git add .	Stage all changes
git commit -m "message"	Commit changes with a message
git push	Push committed changes to the remote
git pull	Pull changes from the remote
Extending the Setup
Create a new container-specific YAML file (e.g., docker-compose.newcontainer.yml).

Include service configurations specific to the container.

Run the combined configuration:

bash
docker-compose -f docker-compose.yml -f docker-compose.newcontainer.yml up -d
Contributing
Contributions are welcome! Please fork the repository, create a new branch, and submit a pull request.


get plex token from inside docker container

docker exec plex \
  sed -n 's/.*PlexOnlineToken="\([^"]*\)".*/\1/p' \
  "/config/Library/Application Support/Plex Media Server/Preferences.xml"
