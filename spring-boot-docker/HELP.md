# Getting Started

### Reference Documentation
For further reference, please consider the following sections:

* [Official Apache Maven documentation](https://maven.apache.org/guides/index.html)
* [Spring Boot Maven Plugin Reference Guide](https://docs.spring.io/spring-boot/docs/2.3.1.RELEASE/maven-plugin/reference/html/)
* [Create an OCI image](https://docs.spring.io/spring-boot/docs/2.3.1.RELEASE/maven-plugin/reference/html/#build-image)
* [Spring Web](https://docs.spring.io/spring-boot/docs/2.3.1.RELEASE/reference/htmlsingle/#boot-features-developing-web-applications)
* [Spring Boot DevTools](https://docs.spring.io/spring-boot/docs/2.3.1.RELEASE/reference/htmlsingle/#using-boot-devtools)

### Guides
The following guides illustrate how to use some features concretely:

* [Building a RESTful Web Service](https://spring.io/guides/gs/rest-service/)
* [Serving Web Content with Spring MVC](https://spring.io/guides/gs/serving-web-content/)
* [Building REST services with Spring](https://spring.io/guides/tutorials/bookmarks/)


### How to run
* `mvn -N io.takari:maven:wrapper` - to create or update all necessary Maven Wrapper
   * `mvn -N io.takari:maven:wrapper -Dmaven=3.3.9` to use a different version of  Maven Wrapper 
After executing the goal, we'll have more files and directories in the project:
   * mvnw: it's an executable Unix shell script used in place of a fully installed Maven
   * mvnw.cmd: it's the Batch version of the above script
   * mvn: the hidden folder that holds the Maven Wrapper Java library and its properties file
* `mvn package && java -jar target/spring-boot-docker-0.0.1-SNAPSHOT.jar`   
   * go to localhost:8100 to see your "Hello from Docker World" message.
* Build own Docker Image   
  * `docker build -t spring-boot-docker .` to build the image
  * `docker run -p 8100:8100 --name spring-boot --rm spring-boot-docker` to run the container form image
  * go to localhost:8100 to see your "Hello from Docker World" message.
* Build a Docker Image with Maven 
  * `mvn spring-boot:build-image -Dspring-boot.build-image.imageName=spring-boot-docker-from-maven` -  to run the Spring Boot image generator without even changing your pom.xml
* Using Spring Profiles
  * `docker run -e "SPRING_PROFILES_ACTIVE=prod" -p 8100:8100 -t spring-boot-docker-from-maven` - to run using 'prod' prfile
* Debugging the application in a Docker container  
  * `docker run -e "JAVA_TOOL_OPTIONS=-agentlib:jdwp=transport=dt_socket,address=5005,server=y,suspend=n" -p 8100:8100 -p 5005:5005 -t spring-boot-docker` - to debug the application JPDA Transport.
  So we’ll treat the container like a remote server.  
