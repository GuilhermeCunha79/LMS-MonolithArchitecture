# 📚 LMS - Monolithic Architecture

This project is a **Library Management System (LMS)** developed as part of the **Software Architecture** course at **ISEP**. The application follows a **monolithic architecture**, built with **Spring Boot**, modern **CI/CD practices**, and supports switching **DBMSs at runtime** through configuration.

---

## ✅ Features

- 📖 Management of books, readers, and loans
- 🔁 Multi-DBMS support via configuration:
  - MySQL
  - SQL Server
  - MongoDB
  - Redis
- 🧪 Automated testing:
  - Unit testing with coverage
  - Mutation testing
- 👤 Authentication with external providers:
  - Google
  - Facebook
  - Azure
- ⚙️ Continuous Integration (CI) with Jenkins
- 🚀 Local and remote deployment (`vs-ctl.dei.isep.ipp.pt`)
- 🧩 Clean layer separation: Domain, Application, Infrastructure

---

## 🛠️ Technologies Used

- Java 21
- Spring Boot
- Maven 3.8.7
- H2 (server mode for testing)
- MySQL / SQL Server / MongoDB / Redis
- Jenkins (CI/CD)
- Docker / Docker Compose
- SonarQube (static analysis)
- Postman (manual testing)

---

## ⚙️ Getting Started

### 🔧 1. Prerequisites

Make sure you have installed:

- Java 21
- Maven 3.8.7
- Docker and Docker Compose (optional but recommended)
- MySQL, SQL Server, MongoDB, or Redis (or use Docker)
- An IDE (e.g., IntelliJ, VS Code)

---

### 📥 2. Clone the Repository

```bash
git clone https://github.com/GuilhermeCunha79/LMS-MonolithArchitecture.git
cd LMS-MonolithArchitecture
```

---

### ⚙️ 3. Configure Properties

Edit the `src/main/resources/application.properties` file:

```properties
# Repository type: JPA or MONGO
repository.type=JPA

# JPA implementation: MYSQL, SQLSERVER, REDIS
repository.jpa.type=MYSQL

# Example configuration for MySQL
spring.datasource.url=jdbc:mysql://localhost:3306/lms
spring.datasource.username=root
spring.datasource.password=admin
spring.jpa.hibernate.ddl-auto=update
```

You can also configure these values using a `.env` file.

---

### 🚀 4. Run the Application

```bash
./mvnw spring-boot:run
```

The application will be available at:

[http://localhost:8080](http://localhost:8080)

---

### 🔐 5. OAuth2 Authentication (Optional)

To enable login with external providers like Google, add the following configuration:

```properties
spring.security.oauth2.client.registration.google.client-id=YOUR_GOOGLE_CLIENT_ID
spring.security.oauth2.client.registration.google.client-secret=YOUR_GOOGLE_CLIENT_SECRET
```

---

### 🧪 6. Running Tests

#### Unit Tests + Coverage

```bash
mvn test
```

#### Mutation Testing (with PIT)

```bash
mvn org.pitest:pitest-maven:mutationCoverage
```

---

### 🤖 CI/CD with Jenkins

This project includes a `Jenkinsfile` with the full CI/CD pipeline:

1. 🔄 Code checkout  
2. 🧪 Testing + code coverage  
3. 🔍 Static analysis (SonarQube)  
4. 📦 Artifact packaging  
5. 🚀 Local or remote deployment  

> Jenkins can run locally or on the remote server: `vs-ctl.dei.isep.ipp.pt`

---

### 🧩 Project Structure

```bash
├── domain         # Domain entities and logic
├── application    # Application use cases
├── infrastructure # Repositories, controllers, auth providers
├── config         # Dynamic runtime configuration
├── tests          # Unit and integration tests
├── Jenkinsfile    # CI/CD pipeline script
```

---

### 🔐 Sample `.env.template` File

```dotenv
REPOSITORY_TYPE=JPA
REPOSITORY_JPA_TYPE=MYSQL

SPRING_DATASOURCE_URL=jdbc:mysql://localhost:3306/lms
SPRING_DATASOURCE_USERNAME=root
SPRING_DATASOURCE_PASSWORD=admin

GOOGLE_CLIENT_ID=your-google-client-id
GOOGLE_CLIENT_SECRET=your-google-client-secret
```

---

### 👥 Authors

- Guilherme Cunha - [@GuilhermeCunha79](https://github.com/GuilhermeCunha79)

---
This project is part of the Master in Software Engineering curriculum at ISEP, developed for ARQSOFT/ODSOFT.
