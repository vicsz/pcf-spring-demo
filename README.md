# Simple Java Spring Boot Demo on PCF

Key features highlighted:

1. Deployments using PCF Push
2. AppsMan Developer Experience
3. Scaling Up
4. Spring Boot Actuator
5. Spring Data with H2 -- Simple Data Rest Endpoint
6. Spring Data with MySQL -- Using PCF Marketplace and Service Binding

## Requirements

1. CF CLI installed
2. Gradle installed
3. Java JDK 1.8+

## Deployments using PCF Push

Build the project:

```sh
gradle build
```

Deploy to PCF

```sh
cf push pcf-demo -p build/libs/pcf-demo-0.0.1-SNAPSHOT.jar
```

## Scaling Up

Demo adding additional instance using PCF (Scale Button)

## Spring Boot Actuator

Note the addition of the following endpoints:

1. /actuator/
2. /actuator/health/
3. /actuator/info/
4. /actuator/logfile/
5. /actuator/env/

Main code addition was the starter-actuator dependency.

## Spring Data with H2 -- Simple Data Rest Endpoint

Note:

http://localhost:8080/api/persons/

Minimal code involved for to get a SQL Rest Endpoint up and running.

Sensible defaults including in-memory H2 database.

Automatic data population (import.sql).




