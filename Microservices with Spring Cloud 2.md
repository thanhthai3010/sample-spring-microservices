### I. Spring Cloud Config
1. Gradle dependencies:
    ```sh
    implementation('org.springframework.cloud:spring-cloud-config-server')
    ```
2. `bootstrap.yml` file config, including application port and where to get config file:
    ```sh
    server:
      port: 8088
      
    spring:
      cloud:
        config:
          server:
            git:
              uri: ${HOME}/data/mcg-config
    ```
    **Note**: `${HOME}/data/mcg-config` is the link to git repository.
3. Add config-server annotation `@EnableConfigServer`:
    ```java
    @SpringBootApplication
    @EnableConfigServer
    public class ConfigServiceApplication {
        public static void main(String[] args) {
    	    SpringApplication.run(ConfigServiceApplication.class, args);
        }
    }
    ```
### II. Service Discovery With Spring Cloud Netflix Eureka
1. Gradle dependencies:
    ```sh
    implementation('org.springframework.cloud:spring-cloud-starter-netflix-eureka-server')
	implementation('org.springframework.cloud:spring-cloud-starter-config')
    ```
2. Add config-server annotation `@EnableEurekaServer`:
    ```java
    @SpringBootApplication
    @EnableEurekaServer
    public class DiscoveryServiceApplication {
        public static void main(String[] args) {
    	    SpringApplication.run(DiscoveryServiceApplication.class, args);
        }
    }
    ```
3. The application has to fetch a property source from the configuration server. The minimal configuration required on the client side is an application name and config server's connection settings.
    ```sh
    spring:
      application:
        name: discovery-service
      cloud:
        config:
          uri: http://localhost:8088
    ```
### III. Microservice Using Spring Boot and Spring Cloud
1. 