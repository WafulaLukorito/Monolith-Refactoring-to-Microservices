# Udagram Image Filtering Application

Image Filtering application, a simpler Instagram version. It allows users to register and log into a web client, post photos to the feed, and process photos using an [image filtering microservice](https://github.com/WafulaLukorito/Image-Filtering-Microservice-API-Endpoint-using-AWS-Elastic-Beanstalk).

I was provided with a monolithic application. I had to refactor the application into microservices and deploy it to AWS.

## Project Tasks
For this project, I carried out the following:

- Refactored the monolithic application into `microservices`.
- Created `s3 bucket` and `RDS database` to store images and user data.
- Set up each microservice to run on separate `Docker` containers.
- Set up a `reverse proxy` server to route requests to the appropriate microservice.
- Set up `CircleCI` as a CI/CD to build and test the application and push images to `DockerHub`.
- Deployed the DockerHub images to the `Elastic Kubernetes Service` (`EKS`) cluster.
- Employed `AWS CLI` to interface programatically with AWS services and `kubectl` to manage the Kubernetes cluster.
- Set up logging and monitoring for the microservices using `kubectl logs`.

## Components

The project has 2 main components:

1. Frontend Web App - `Angular` web application built with `Ionic Framework`
![Frontend](https://github.com/WafulaLukorito/Monolith-Refactoring-to-Microservices/blob/master/screenshots/Screenshot%202022-12-08%20003021.png?raw=true "Frontend")
2. Backend RESTful API - A `Node-Express` application with a `Postgres` database

## Refactoring the Monolithic Application

- Initial API contained logic for both `users` and `feed` endpoints. I had to refactor the API into two separate microservices that can be run independently.
- Configured the Dockerfile for the frontend service.
- Created a reverse proxy running the `Nginx` server to route requests between frontend and the appropriate microservices.

## Continuous Integration Pipeline
- Created respective DockerHub repositories for each microservice.
- Set up `CircleCI` to build and test the application and push images to `DockerHub`.
![DockerHub](https://github.com/WafulaLukorito/Monolith-Refactoring-to-Microservices/blob/master/screenshots/Screenshot%20dockerhub.png?raw=true "DockerHub")
![CircleCI](https://github.com/WafulaLukorito/Monolith-Refactoring-to-Microservices/blob/master/screenshots/Screenshot%20circle%20ci.png?raw=true "CircleCI")

## Container Orchestration
- Created a `Kubernetes` cluster on `AWS EKS` and respective `NodeGroups` using `kubectl`.
- Deployed the DockerHub images to the `EKS` cluster.
- Connected k8s services to allow communication between the microservices.
![Kubernetes get services](https://github.com/WafulaLukorito/Monolith-Refactoring-to-Microservices/blob/master/screenshots/kubernetes%20services%20shows%20a%20reverse%20proxy.png?raw=true "Kubernetes get services")

***More screenshots are in the screenshots folder***