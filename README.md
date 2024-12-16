# Udemy Ranga - learn spring boot
## Section 10 Appendix Introduction to Spring Boot in 12 Steps
From the course Master Microservice with Spring Boot and Spring Cloud  
https://globallogic.udemy.com/course/microservices-with-spring-boot-and-spring-cloud/learn/lecture/32398358#content

### 1 - Profiles
Application has different environments: Dev, Prod <br>
application.properties - default <br>
```
spring.profiles.active=prod (or dev)
```
application-dev.properties <br>
application-prod.properties

### 2 - ConfigurationProperties
http://localhost:8080/currency-configuration
response
```
{
   "url": "http://default.in28minutes.com",
   "userName": "defaultusername",
   "key": "default"
}
```
### 3 - Embedded Services
Simple alternative to Web/Application Server inside of Spring Boot
- Step 1: Install Java
- Step 2: Run JAR file (not WAR)
- Embedded Server Example: 
  - spring-boot-starter-tomcat (default)
  - spring-boot-starter-jetty
  - spring-boot-starter-undertow

### 4 - Actuator
Monitor and manage your application in your production
- beans
- health
- metrics
- mappings
```
management.endpoints.web.exposure.include=*
```
http://localhost:8080/actuator/health/ <br>
http://localhost:8080/actuator/configprops <br>
http://localhost:8080/actuator/metrics <br>
http://localhost:8080/actuator/metrics/http.server.requests <br>
Ex.:
```
{
  "name": "http.server.requests",
  "baseUnit": "seconds",
  "measurements": [
    {
      "statistic": "COUNT",
      "value": 5
    },
    {
      "statistic": "TOTAL_TIME",
      "value": 0.2032701
    },
    {
      "statistic": "MAX",
      "value": 0.0047994
    }
  ],
  "availableTags": [
    {
      "tag": "exception",
      "values": [
        "none"
      ]
    },
    {
      "tag": "method",
      "values": [
        "GET"
      ]
    },
    {
      "tag": "error",
      "values": [
        "none"
      ]
    },
    {
      "tag": "uri",
      "values": [
        "/actuator/configprops",
        "/actuator/health/**",
        "/actuator/metrics",
        "/**"
      ]
    },
    {
      "tag": "outcome",
      "values": [
        "CLIENT_ERROR",
        "SUCCESS"
      ]
    },
    {
      "tag": "status",
      "values": [
        "404",
        "200"
      ]
    }
  ]
}
```