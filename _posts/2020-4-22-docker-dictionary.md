---
layout: post
title: Docker Dictionary
tags: devops docker
---

When you start learning Docker, it's easy to get overwhelmed by all the new jargon that gets thrown at you. It's good to have a central repository of all the new words that one will encounter navigating this fascinating new territory. Here are some of the important concepts in Docker.

**Image**: A package with all the dependencies and information needed to create a container. An image includes all the dependencies (such as frameworks) plus deployment and execution configuration used by a container runtime. Usually, an image derives from multiple base images that are layers stacked on top of each other to form the container's filesystem. An image is immutable once it has been created.


**Container**: An instance of a Docker image. A container represents the execution of a single application, process, or service. It consists of a Docker image, an execution environment, and a standard set of instructions. When scaling a service, you create multiple instances of a container from the same image. Or a batch job can create multiple containers from the same image, passing different parameters to each instance.

**Dockerfile**: A text file that contains instructions for how to build a Docker image. It's like a batch script; the first line states the base image to begin with and then follows the instructions to install required programs, copy files and so on until you get the working environment you need.

**Build**: The action of building a container image based on the information and context provided by its Dockerfile, plus additional files in the folder where the image is built. 

**Volumes**: Offer a writable filesystem that the container can use. Since images are read-only, but most programs need to write to the filesystem, volumes add a writable layer on top of the container image. The programs have access to a writable filesystem. The program doesn't know it is accessing a layered filesystem; it is just the filesystem as usual. Volumes live in the host system and are managed by Docker.

**Tag**: A mark or label you can apply to images to identify different images or versions of the same image (depending on the version number or the target environment).

**Repository (repo)**: A collection of related Docker images, labelled with a tag that indicates the image version. Some repos contain multiple variants of a specific image, such as an image containing SDKs (heavier), an image containing only runtimes (lighter), etc. Those variants can be marked with tags. A single repo can contain platform variants, such as a Linux image and a Windows image.

**Registry**: A service that provides access to repositories. The default registry for most public images is [Docker Hub](https://hub.docker.com/) (owned by Docker as an organization). A registry usually contains repositories from multiple teams. Companies often have private registries to store and manage images they've created. Azure Container Registry is another example.

**Docker Hub**: A public registry to upload images and work with them. Docker Hub provides Docker image hosting, public or private registries, build triggers and webhooks, and integration with GitHub and Bitbucket.

**Azure Container Registry**: A private container registry stored in Azure. You can configure it to allow restricted access to your team or company.

**Compose**: A command-line tool and YAML file format with metadata for defining and running multi-container applications. You define a single application based on multiple images with one or more .yml files that can override values depending on the environment. After you have created the definitions, you can deploy the whole multi-container application with a single command (docker-compose up) that creates a container per image on the Docker host.

**Cluster**: A collection of Docker hosts exposed as if it were a single virtual Docker host so that the application can scale to multiple instances of the services spread across multiple hosts within the cluster. Docker clusters can be created with Kubernetes, Azure Service Fabric, Docker Swarm and Mesosphere DC/OS.

**Orchestrator**: A tool that simplifies the management of clusters and Docker hosts. Orchestrators enable you to manage their images, containers, and hosts through a CLI or a graphical UI. You can manage container networking, configurations, load balancing, service discovery, high availability, Docker host configuration, and more. An orchestrator is responsible for running, distributing, scaling, and healing workloads across a collection of nodes.

Source:[ Docker Terminology](https://docs.microsoft.com/en-us/dotnet/architecture/microservices/container-docker-introduction/docker-terminology)