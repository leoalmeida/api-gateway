# API Gateway

![Java](https://img.shields.io/badge/Java-17-007396?logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.5.4-6DB33F?logo=springboot&logoColor=white)
![Spring Cloud](https://img.shields.io/badge/Spring_Cloud-2025.0.0-6DB33F?logo=spring&logoColor=white)
![Eureka Client](https://img.shields.io/badge/Eureka-Client-E50914?logo=netflix&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-3.9%2B-C71A36?logo=apachemaven&logoColor=white)
![JaCoCo](https://img.shields.io/badge/JaCoCo-Coverage-success)
![Codecov](https://img.shields.io/badge/Codecov-enabled-F01F7A?logo=codecov&logoColor=white)

[PT-BR](README.md) | [EN](README.en.md)

Gateway module of the voting ecosystem, built with Spring Cloud Gateway and integrated with Eureka for dynamic service routing.

## Overview

- Project: `gateway`
- Default port: `8082`
- Service registry: `http://localhost:8761/eureka/`
- Java: `17`
- Spring Boot: `3.5.4`
- Spring Cloud: `2025.0.0`

## Tech Stack

- Spring Boot
- Spring Cloud Gateway
- Eureka Client (Netflix)
- Maven
- JaCoCo
- Checkstyle
- PMD
- SpotBugs
- Spotless

## Requirements

- JDK 17
- Maven 3.9+ (or use wrapper `mvnw`)

## Configuration

Main config file: `src/main/resources/application.properties`

```properties
server.port=8082
spring.application.name=gateway
eureka.client.serviceUrl.defaultZone=http://localhost:8761/eureka/
spring.cloud.gateway.discovery.locator.enabled=true
spring.cloud.gateway.discovery.locator.lower-case-service-id=true
```

## Run Locally

### Windows (PowerShell)

```powershell
.\mvnw spring-boot:run
```

### Linux/macOS

```bash
./mvnw spring-boot:run
```

## Build and Tests

```bash
./mvnw clean package
```

## Code Quality

```bash
./mvnw spotless:check
./mvnw checkstyle:check
./mvnw pmd:check
./mvnw spotbugs:check
```

## Test Coverage

```bash
./mvnw jacoco:report
```

Report location:

- `target/site/jacoco/index.html`

## CI Pipeline

Main workflow:

- `.github/workflows/workflow-backend-gateway.yml`

Main stages:

- Lint/quality: Spotless, Checkstyle, PMD, SpotBugs
- Tests + JaCoCo
- Codecov upload
- Artifact build (`target/*.jar`)

## Integrated Execution

1. Start `service-discovery` first (port `8761`).
2. Start business microservices.
3. Start `api-gateway`.
4. Validate routing through the gateway.

## Useful Endpoints

- Actuator health: `http://localhost:8082/actuator/health`
- Eureka dashboard: `http://localhost:8761/`

## License

Internal usage for study/challenge purposes.
