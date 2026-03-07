# 🌿 AGMS Centralized Configuration Repository

This repository serves as the **Single Source of Truth** for the configurations of the **Automated Greenhouse Management System (AGMS)**. It is utilized by the **Spring Cloud Config Server** to externalize and manage application properties for each microservice independently.

## 📂 Repository Structure

The repository contains dedicated YAML configuration files for each microservice and infrastructure component. This structure ensures **configuration isolation**, where changes to one service do not affect others:

- **`api-gateway.yml`**: Manages routing rules, JWT secret keys for token validation, and CORS policies.
- **`auth-service.yml`**: Contains MySQL database settings for identity management and JWT signing properties.
- **`zone-service.yml`**: Defines database configurations for greenhouse zones and inter-service communication settings.
- **`sensor-service.yml`**: Stores sensitive credentials for the External IoT Data Provider API and configurations for the telemetry scheduling task.
- **`automation-service.yml`**: Manages database settings for the rule engine and automation action logging.
- **`crop-service.yml`**: Defines inventory database settings and crop growth lifecycle stage definitions.

## ⚙️ Integration with AGMS Architecture

The **Spring Cloud Config Server (Port 8888)** is configured to fetch properties from this Git repository. During the **Bootstrap phase** of any microservice startup:

1. The service identifies itself using its `spring.application.name`.
2. It requests its specific configuration file from the Config Server.
3. The Config Server serves the corresponding `.yml` file from this repository, ensuring the service starts with the latest environment-specific settings.

## 🔄 Why Service-Specific Configuration?

- **Isolation**: Each service has its own configuration file, reducing the risk of global configuration errors.
- **Maintainability**: Update database credentials, API keys, or business rules in a single file without affecting the entire system.
- **Cloud-Native Design**: Facilitates independent scaling and deployment of microservices by externalizing environment properties.

## 🛠️ Requirements
- **Config Server Port**: 8888
- **Format**: YAML (Indentation sensitive)
- **Branch**: main

---
*Developed as part of the Graduate Diploma in Software Engineering (GDSE) - Software Architectures & Design Patterns II Final Assignment.*
