# Spring Boot Microservice with SonarQube Integration

A lightweight Spring Boot application featuring an H2 In-Memory database and a dedicated SonarQube environment for static code analysis.

#  Prerequisites

Before running the application, ensure you have the following installed:

- Java 17 or higher
- Maven 3.8+
- Docker & Docker Compose (for SonarQube)

# Getting Started

1. Start SonarQube Instance

The project includes a pre-configured Docker Compose file to spin up SonarQube.

```bash
cd sonarqube-docker
docker-compose up -d
```

- Access: http://localhost:9000

Default Credentials: Login: admin | Password: admin (You will be prompted to change it on first login).

2. Run the Application

You can start the Spring Boot application using the Maven wrapper:

```bash
./mvnw spring-boot:run
```


3. H2 Database Console

The application uses an H2 In-Memory database. You can access the console to inspect data at:

- URL: http://localhost:8080/h2-console
- JDBC URL: jdbc:h2:mem:testdb
- User: sa
- Password: (Keep empty or as defined in application.properties)

# Running SonarQube Analysis

Once the SonarQube container is healthy and the application is ready, execute the following command to run the analysis:

```bash
mvn clean verify sonar:sonar \
  -Dsonar.projectKey=my-spring-project \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.login=YOUR_GENERATED_TOKEN
```

Note: Generate your SONAR_TOKEN in the SonarQube Dashboard under My Account > Security.