# 📌 PostgreSQL mit Docker & Docker Compose einrichten

Diese Anleitung zeigt, wie du PostgreSQL mit Docker installierst und startest.

---

## 🛠 1. Voraussetzungen

Installiere folgende Tools:

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

---

## 📄 2. `docker-compose.yaml` erstellen

Erstelle eine Datei `docker-compose.yaml` im Projektordner:

```yaml
version: "3.8"
services:
  postgres:
    image: postgres:latest
    container_name: my_postgres
    restart: always
    environment:
      POSTGRES_USER: myuser
      POSTGRES_PASSWORD: mypassword
      POSTGRES_DB: mydatabase
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

## 3. Docker-Container starten

Starte den PostgreSQL-Container:

```sh
Kopieren
Bearbeiten
docker-compose up -d
-d startet den Container im Hintergrund.
Prüfe, ob der Container läuft:
sh
Kopieren
Bearbeiten
docker ps
Falls du den Container stoppen möchtest:
```

```sh
Kopieren
Bearbeiten
docker-compose down
```

## 🔗 4. Verbindung zur Datenbank

Nutze folgende DATABASE_URL für deine Anwendung (z. B. .env Datei):

```env
Kopieren
Bearbeiten
DATABASE_URL=postgresql://myuser:mypassword@localhost:5432/mydatabase
Falls du Docker in einem anderen Netzwerk nutzt, ersetze localhost durch den passenden Hostnamen.
```

## 📎 Nützliche Links

```

🔹 PostgreSQL Docker Image
🔹 Docker-Compose Dokumentation

```

# Docker Image for PostgreSQL

## Required Packages:

- docker
- docker-compose

### Files:

- `.dockerignore`
- `docker-compose.yml`
- `Dockerfile.dev`

### Commands:

- `docker-compose up --build`
- `docker ps`

### Docker Service Management:

- `sudo systemctl start docker`
- `sudo systemctl enable docker`
- `sudo usermod -aG docker $USER`
- `newgrp docker`

### Build and Start with Docker Compose:

- `docker-compose -f ./docker-compose.yml up --build`

# Env Datei

```
# Authentication Docker

POSTGRES_USER=myuser
POSTGRES_PASSWORD=mypassword
POSTGRES_DB=authdb
HOST_PORT=5432 # ist dockerfile abhängig
POSTGRES_PORT=5432
```
