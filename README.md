# Devices Tracking System - Application Deployment
The Devices Tracking System is an application built for aggregating GPS positions of registered devices and visualising
their routes on a map. The whole system is composed of the following components:
  - a mobile application for pushing GPS positions of any device
  - a web application for displaying routes of tracked devices
  - a distributed architecture for aggregating and processing collected GPS data.

## Prerequisites:
You need to have the following tools installed and configured:
  - Java SE 1.8+
  - Maven 3.0+
  - MongoDB 3.0+
  - RabbitMQ Server 3.0+

## Architecture Overview
![Architecture Overview](https://lh5.googleusercontent.com/alDXk75dCQZM8GS3ef-eFVDsDClti4qx1QpP86uYv-KHeO1KJUipUodKhIRBJw4zK_n2BNS15WgoNQ=w1366-h662-rw)

## Project setup for local development
In order to set up the whole infranstructure locally, follow these steps:
  1. Run the [Configuration Server](https://github.com/device-tracking-system/configuration-server). After successful
     installation, the Spring Cloud Config server is running on:
```
http://localhost:8888
```
  2. Run the [Service Discovery](https://github.com/device-tracking-system/service-discovery). After successful 
     installation, the Eureka discovery service is running on:
```
http://localhost:8080/eureka
```
while the service discovery dashboard is running on:
```
http://localhost:8080
```
  3. Run the [Processing Service](https://github.com/device-tracking-system/processing-service). This microservice
     do not expose antyhing to the Web.
  4. Run the [UI Service](https://github.com/device-tracking-system/ui-service). After successful installation,
     the microservice hosting the web application is running on:
```
http://localhost:8081
```
  5. Run the [Edge Server](https://github.com/device-tracking-system/edge-server) - remember to set up required
     environment variables before. After successful installation, the Zuul proxy is running on:
```
http://localhost (default HTTP 80 port)
```

## Deployment
This project is deployed to a cloud infrastructure hosted by the Google Cloud Platform. In order to deploy a new 
version of the platform, follow these steps:
  1. Build Docker images for all the microservices as defined in appropriate repositories.
  2. Deploy the images to the Docker Hub by typing:
```
docker login --username [Your username in Docker Hub] --password [Your password to Docker Hub]
docker tag [image name] [image tag]
docker push [Your username in Docker Hub]/[repository name]
```
where `[image tag]` is given by `[Your username in Docker Hub]/[repository name]`.

  3. Log in to the Google Cloud Platform account.
  4. Download latest versions of images from the Docker Hub and run them in containers as defined in appropriate
  repositories. When setting up the infrastructure, follow instructions presented in the previous section.

