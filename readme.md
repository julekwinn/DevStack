# DevStack: Comprehensive Development Environment

## Table of Contents

1. [Introduction](#introduction)
2. [Features](#features)
3. [Prerequisites](#prerequisites)
4. [Installation](#installation)
5. [Usage](#usage)
6. [Components](#components)
   - [Systems](#systems)
   - [Databases](#databases)
   - [Tools](#tools)
   - [Stream Processing](#stream-processing)
   - [Web Servers](#web-servers)
7. [Accessing Services](#accessing-services)
8. [Configuration](#configuration)
9. [Troubleshooting](#troubleshooting)
10. [License](#license)

## Introduction

DevStack is a comprehensive, Docker-based development environment that provides a full suite of tools and services for software development, testing, and deployment. With a single command, you can spin up a complete stack of development tools, databases, monitoring solutions, and more.

This project aims to simplify the setup process for developers, allowing them to focus on coding rather than environment configuration. It's perfect for individual developers, teams, and educational purposes.

## Features

- **One-Click Setup**: Launch a complete development environment with a single `docker-compose up` command.
- **Comprehensive Tool Suite**: Includes popular databases, monitoring tools, CI/CD solutions, and more.
- **Isolated Environments**: Each service runs in its own Docker container, ensuring isolation and ease of management.
- **Persistence**: Data is persisted across container restarts using Docker volumes.
- **Customizable**: Easily modify the `docker-compose.yml` file to add, remove, or customize services.
- **Web-Based Management**: Many services include web-based management interfaces for easy administration.
- **Network Isolation**: All services are connected to a custom Docker network for secure inter-service communication.

## Prerequisites

- Docker
- Docker Compose
- Git (for cloning the repository)

## Installation

1. Clone the repository:
   ```
   git clone https://github.com/yourusername/devstack.git
   ```
2. Navigate to the project directory:
   ```
   cd devstack
   ```

## Usage

To start the entire DevStack:

```
docker-compose up -d
```

To stop and remove all containers:

```
docker-compose down
```

To view logs for all services:

```
docker-compose logs
```

To view logs for a specific service:

```
docker-compose logs [service_name]
```

## Components

### Systems

1. **Ubuntu Containers (x3)**

   - Purpose: General-purpose Linux environments
   - Ports: 2222, 2223, 2224 (SSH), 8081, 8082, 8083 (HTTP)

2. **Kali Linux**
   - Purpose: Security testing and penetration testing
   - Port: 2225 (SSH)

### Databases

1. **MongoDB**

   - Purpose: NoSQL database
   - Port: 27017
   - Web UI: Mongo Express (Port 8096)

2. **PostgreSQL**

   - Purpose: Relational database
   - Port: 5432
   - Web UI: pgAdmin (Port 8085)

3. **Redis**

   - Purpose: In-memory data structure store
   - Port: 6379
   - Web UI: Redis Commander (Port 8087)

4. **InfluxDB**

   - Purpose: Time series database
   - Port: 8086

5. **Elasticsearch**
   - Purpose: Search and analytics engine
   - Ports: 9200 (REST API), 9300 (Transport)

### Tools

1. **Checkmk**

   - Purpose: Infrastructure monitoring
   - Port: 6069

2. **Grafana**

   - Purpose: Data visualization and monitoring
   - Port: 3000

3. **RabbitMQ**

   - Purpose: Message broker
   - Ports: 5672 (AMQP), 15672 (Management UI)

4. **MinIO**

   - Purpose: S3-compatible object storage
   - Ports: 9000 (API), 9001 (Web UI)

5. **Jenkins**

   - Purpose: Continuous Integration/Continuous Deployment
   - Ports: 8084 (Web UI), 50000 (Agent)

6. **Metabase**

   - Purpose: Business intelligence and analytics
   - Port: 3001

7. **SonarQube**

   - Purpose: Code quality and security analysis
   - Port: 9002

8. **Prometheus**

   - Purpose: Monitoring and alerting
   - Port: 9090

9. **Kibana**

   - Purpose: Data visualization for Elasticsearch
   - Port: 5601

10. **Logstash**
    - Purpose: Log processing pipeline
    - Port: 5000

### Stream Processing

1. **Apache Kafka**

   - Purpose: Distributed event streaming platform
   - Port: 9092

2. **ZooKeeper**
   - Purpose: Distributed coordination service (used by Kafka)
   - Port: 2181

### Web Servers

1. **Static Web Server**
   - Purpose: Hosts a static website
   - Port: 6969

## Accessing Services

Most services can be accessed through their web interfaces. Here's a quick reference:

- Checkmk: http://localhost:6069
- Mongo Express: http://localhost:8096
- Grafana: http://localhost:3000
- RabbitMQ Management: http://localhost:15672
- MinIO Console: http://localhost:9001
- Jenkins: http://localhost:8084
- Metabase: http://localhost:3001
- pgAdmin: http://localhost:8085
- SonarQube: http://localhost:9002
- Prometheus: http://localhost:9090
- Kibana: http://localhost:5601
- Static Website: http://localhost:6969

For services without web interfaces, use the appropriate client tools and the exposed ports to connect.

## Configuration

- Environment variables and other configurations are set in the `docker-compose.yml` file.
- Some services have their configuration files mounted as volumes. You can find these in the `shared` directory.
- To modify service configurations, update the respective files in the `shared` directory or the environment variables in `docker-compose.yml`.

## Troubleshooting

1. **Service fails to start**:

   - Check the logs using `docker-compose logs [service_name]`
   - Ensure all required ports are free on your host machine
   - Verify that the service's dependencies are running

2. **Cannot connect to a service**:

   - Ensure the service is running (`docker-compose ps`)
   - Check if the port is correctly mapped in `docker-compose.yml`
   - Verify your firewall settings

3. **Data persistence issues**:
   - Check the volume configurations in `docker-compose.yml`
   - Ensure the `shared` directory has the correct permissions

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.
