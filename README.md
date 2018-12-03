Microservices example with Spring Boot 2.0, Eureka and Spring Cloud

1. Build jar for each service:
- ```cd /project_name```
- ```gradle build```
2. Run jar file with command:
- ```cd build/libs/```
- ```java -jar project_name-0.0.1-SNAPSHOT.jar ```
3. In the case of `employee-service` you can easily run two instances of the same service locally based on remote properties `employee-service-instance2.yml` :
- ```cd employee-service/build/libs/```
- ``` java -jar employee-service-0.0.1-SNAPSHOT.jar --spring.profiles.active=instance2 ```
