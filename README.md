# sTMS - Student Transportation Management System

A full-stack application with Spring Boot backend, React frontend, and PostgreSQL database.

## Architecture

- **API**: Spring Boot 3.5.7 with Java 25
- **Web**: React 19 with Vite
- **Database**: PostgreSQL 16

## Prerequisites

- Docker
- Docker Compose

## Getting Started

### Using Docker Compose (Recommended)

1. **Start all services**:
```bash
docker-compose up -d
```

2. **View logs**:
```bash
# All services
docker-compose logs -f

# Specific service
docker-compose logs -f api
docker-compose logs -f web
docker-compose logs -f db
```

3. **Stop all services**:
```bash
docker-compose down
```

4. **Stop and remove volumes** (WARNING: This will delete all data):
```bash
docker-compose down -v
```

### Access the Application

- **Web Frontend**: http://localhost
- **API Backend**: http://localhost:8080
- **PostgreSQL**: localhost:5432
  - Database: `stms`
  - Username: `stms_user`
  - Password: `stms_password`

## Development

### API Development

```bash
cd api
./mvnw spring-boot:run
```

### Web Development

```bash
cd web
npm install
npm run dev
```

## Docker Commands

### Rebuild containers after code changes:
```bash
docker-compose up -d --build
```

### View running containers:
```bash
docker-compose ps
```

### Execute commands in containers:
```bash
# Access PostgreSQL
docker-compose exec db psql -U stms_user -d stms

# Access API container
docker-compose exec api bash

# Access Web container
docker-compose exec web sh
```

### Clean up everything:
```bash
docker-compose down -v --rmi all
```

## Troubleshooting

### Port conflicts
If you get port conflict errors, modify the ports in `docker-compose.yml`:
```yaml
ports:
  - "8081:8080"  # Change left side to different port
```

### Database connection issues
Check if the database is healthy:
```bash
docker-compose ps db
```

### API not starting
Check API logs:
```bash
docker-compose logs api
```

## Environment Variables

You can customize environment variables in `docker-compose.yml`:

- `POSTGRES_DB`: Database name
- `POSTGRES_USER`: Database user
- `POSTGRES_PASSWORD`: Database password
- `SPRING_JPA_HIBERNATE_DDL_AUTO`: Hibernate DDL mode (create, update, validate, none)

## Project Structure

```
sTMS/
├── api/                    # Spring Boot backend
│   ├── src/
│   ├── pom.xml
│   └── Dockerfile
├── web/                    # React frontend
│   ├── src/
│   ├── package.json
│   ├── nginx.conf
│   └── Dockerfile
└── docker-compose.yml      # Docker orchestration
```

