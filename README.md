# API Gateway

![Java](https://img.shields.io/badge/Java-17-007396?logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.5.4-6DB33F?logo=springboot&logoColor=white)
![Spring Cloud](https://img.shields.io/badge/Spring_Cloud-2025.0.0-6DB33F?logo=spring&logoColor=white)
![Eureka Client](https://img.shields.io/badge/Eureka-Client-E50914?logo=netflix&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-3.9%2B-C71A36?logo=apachemaven&logoColor=white)
![JaCoCo](https://img.shields.io/badge/JaCoCo-Coverage-success)
![Codecov](https://img.shields.io/badge/Codecov-enabled-F01F7A?logo=codecov&logoColor=white)

[PT-BR](README.md) | [EN](README.en.md)

API Gateway do ecossistema de votacao, construido com Spring Cloud Gateway e integrado ao Eureka para roteamento dinamico de servicos.

## Visao geral

- Projeto: `gateway`
- Porta padrao: `8082`
- Registro de servicos: `http://localhost:8761/eureka/`
- Java: `17`
- Spring Boot: `3.5.4`
- Spring Cloud: `2025.0.0`

## Tecnologias

- Spring Boot
- Spring Cloud Gateway
- Eureka Client (Netflix)
- Maven
- JaCoCo
- Checkstyle
- PMD
- SpotBugs
- Spotless

## Requisitos

- JDK 17
- Maven 3.9+ (ou uso do wrapper `mvnw`)

## Configuracao

Arquivo principal: `src/main/resources/application.properties`

```properties
server.port=8082
spring.application.name=gateway
eureka.client.serviceUrl.defaultZone=http://localhost:8761/eureka/
spring.cloud.gateway.discovery.locator.enabled=true
spring.cloud.gateway.discovery.locator.lower-case-service-id=true
```

## Executar localmente

### Windows (PowerShell)

```powershell
.\mvnw spring-boot:run
```

### Linux/macOS

```bash
./mvnw spring-boot:run
```

## Build e testes

```bash
./mvnw clean package
```

## Qualidade de codigo

```bash
./mvnw spotless:check
./mvnw checkstyle:check
./mvnw pmd:check
./mvnw spotbugs:check
```

## Cobertura de testes

```bash
./mvnw jacoco:report
```

Relatorio gerado em:

- `target/site/jacoco/index.html`

## Pipeline CI

Workflow principal:

- `.github/workflows/workflow-backend-gateway.yml`

Etapas principais:

- Lint/qualidade: Spotless, Checkstyle, PMD, SpotBugs
- Testes + JaCoCo
- Upload para Codecov
- Build de artefato (`target/*.jar`)

## Execucao integrada

1. Suba o `service-discovery` primeiro (porta `8761`).
2. Suba os microsservicos de negocio.
3. Suba o `api-gateway`.
4. Valide o roteamento via gateway.

## Endpoints uteis

- Health (Actuator): `http://localhost:8082/actuator/health`
- Eureka Dashboard: `http://localhost:8761/`

## Licenca

Uso interno para fins de estudo/desafio.
