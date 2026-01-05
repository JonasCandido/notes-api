# notes-api
The application provides operations for managing notes and uses Nginx to act as a reverse proxy. The entire stack runs using Docker and Docker Compose, making the environment consistent and easy to reproduce.

---

## 🏗️ Features

- Create, read, and delete notes
- PostgreSQL database integration
- Reverse proxy with Nginx
- Dockerized environment with Docker Compose
- Continuous Integration (CI) using GitHub Actions

---

## 🗂️ Project Structure
```
notes-api/
│
├── backend/ # Spring Boot API
│ ├── src/main/java/com/jonas/notesapi/
│ │ ├── controller/ # REST controllers
│ │ ├── model/ # JPA entities
│ │ └── repository/ # Data repositories
│ ├── src/main/resources/application.properties
│ ├── Dockerfile
│ └── pom.xml
│
├── nginx/ # Nginx configuration
│ └── nginx.conf
│
├── docker-compose.yml
└── .github/workflows/ci.yml
```

## 🚀 Requirements

- Docker & Docker Compose
- Java 17
- Maven
- GitHub account for CI (optional)

---

## 🐳 Running the Application with Docker

1. **Build the backend**:

```bash
cd backend
mvn clean package
```

2.  **Start all services**:
```
cd ..
docker compose up --build
```

3. Acess the API via Nginx:

- List
```
curl http://localhost/api/notes
```
- Create
```
curl -X POST http://localhost/api/notes \
  -H "Content-Type: application/json" \
  -d '{"title":"First Note","content":"Hello World"}'
```
- Delete
```
curl -X DELETE http://localhost/api/notes/{id}
```

