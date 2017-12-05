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
  3. Run the [Processing Service](https://github.com/device-tracking-system/processing-service). After successful
     installation, this microservice is running on:
```
http://localhost:8082
```
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

