# Simple Java Spring Boot Demo on PCF

Key features highlighted:

1. Deployments using PCF Push
2. AppsMan Developer Experience
3. Spring Boot Actuator
4. Scaling Up
5. High Availability
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

Hit the index page ..

Note usage of VCAP environment variables.

## AppsMan Developer Experience

Note:

PCF Metrics, including Logging

Tentative Alerting Support

## Spring Boot Actuator

Note the addition of the following endpoints:

1. /actuator/
2. /actuator/health/
3. /actuator/info/
4. /actuator/logfile/
5. /actuator/env/

Main code addition was the starter-actuator dependency.

In PCF, note the GIT property at the top right to identify what's deployed.

Also note the Health Check Information in the GUI.

## Scaling Up

Demo adding additional instance using PCF (Scale Button)

## High Availability

What happens when a JVM crashes or runs out memory ?

Simulate a crash by hitting the /kill endpoint on PCF.

Observe the logs .. note auto-recovery.

## Spring Data with H2 -- Simple Data Rest Endpoint

Note:

http://localhost:8080/api/persons/

Minimal code involved for to get a SQL Rest Endpoint up and running.

Sensible defaults including in-memory H2 database.

Automatic data population (import.sql) and schema creation.

Boilerplate code reduction with Lombok and Data Annotation.

Note that database also works in PCF, we can also check the /actuator/health endpoint for details.

## Spring Data with MySQL -- Using PCF Marketplace and Service Binding

Check the marketplace for available *on-demand , and self-serve* services.

```sh
cf marketplace
```

Note different plans.

In PWS lets create a small MySQL instance:

```sh
cf create-service cleardb spark mydb
```

We also need to bind the service to our application:

```sh
cf bind-service pcf-demo mydb
```

and restart:

```sh
cf restage pcf-demo
```

Note updated /actuator/health endpoint.
