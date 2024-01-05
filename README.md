# Introduction

- The service discovery pattern is used to abstract away the physical location of services.

- A service discovery engine such as Eureka can seamlessly add and remove service instances from an environment without the
  service clients being impacted.

- Client-side load balancing can provide an extra level of performance and resiliency by caching the physical location
  of a service on the client making the service call.

- Eureka is a Netflix project that when used with Spring Cloud, is easy to set up
  and configure.

- You used three different mechanisms in Spring Cloud, Netflix Eureka, and Netflix Ribbon to invoke a service.
  These mechanisms included:

  – Using a Spring Cloud service DiscoveryClient
  – Using Spring Cloud and Ribbon-backed RestTemplate
  – Using Spring Cloud and Netflix’s Feign client


The example code introduces the concept of service registration and discovery patterns using Spring Cloud and Netflix's Eureka server.  Using service discovery, you will be able to add and remove service instances without the clients having to know the physical locations of the service.


1.  A Spring Cloud Config server that is deployed as Docker container and can manage a services configuration information using a file system or GitHub-based repository.
2.  A Eureka server running as a Spring-Cloud based service.  This service will allow multiple service instances to register with it.  Clients that need to call a service will use Eureka to lookup the physical location of the target service.
3.  A organization service that will manage organization data used within EagleEye.
4.  A licensing service that will manage licensing data used within EagleEye.
5.  A Postgres SQL database used to hold the data for these two services.

# Software needed
1.	Apache Maven (http://maven.apache.org). 
2.	Docker (http://docker.com). 
3.	Git Client (http://git-scm.com).


# Building the Docker Images 

Run the following maven command.  This command will execute the [Spotify docker plugin](https://github.com/spotify/docker-maven-plugin) defined in the pom.xml file.  

   **mvn clean package docker:build**

Running the above command at the root of the project directory will build all of the projects.  If everything builds successfully you should see a message indicating that the build was successful.

# Running the services 

Now we are going to use docker-compose to start the actual image.  To start the docker image, issue the following docker-compose command:

   **docker-compose -f docker/common/docker-compose.yml up**

If everything starts correctly you should see a bunch of Spring Boot information fly by on standard out. 
