# Stock Portfolio App

A Dockerized Laravel stock portfolio application.

## Tech Stack

- Laravel
- PHP 8.3 FPM
- Nginx
- MySQL 8
- Docker
- Docker Compose
- Node.js / npm / Vite

---

# Project Structure

```text
.
├── docker-compose.yml
├── dockerfiles/
│   ├── nginx.dockerfile
│   └── php.dockerfile
├── nginx/
│   └── nginx.conf
├── env/
│   └── mysql.env
└── src/
    └── Laravel Application
```

---

# Docker Setup

## Clone Project

```bash
git clone <repository-url>
cd stockfolio
```

---

# Start Containers

## Build Images

```bash
docker compose build
```

## Start Services

```bash
docker compose up -d
```

---

# Install Laravel Dependencies

## Enter App Container

```bash
docker compose exec app sh
```

## Install Composer Dependencies

```bash
composer install
```

## Install Node Dependencies

```bash
npm install
```

---

# Laravel Setup

## Generate App Key

```bash
php artisan key:generate
```

## Create Database Tables

```bash
php artisan migrate
```

# Frontend Development

## Start Vite Development Server

```bash
npm run dev
```

---

# Access Application

Application URL:

```text
http://localhost:8000
```

---

# Database Access

Recommended tools:

- DBeaver
- MySQL Workbench

## MySQL Connection

| Setting | Value |
|---|---|
| Host | localhost |
| Port | 3306 |
| Database | stock_portfolio |
| Username | stock_portfolio |
| Password | portfolio890 |

---

# Useful Docker Commands

## View Running Containers

```bash
docker ps
```


## Remove Containers and Volumes

```bash
docker compose down -v
```

---

# Nginx + PHP-FPM

Nginx acts as a reverse proxy and forwards PHP requests to the Laravel app container using FastCGI.

Example:

```nginx
fastcgi_pass app:9000;
```

Laravel routes are handled through:

```nginx
try_files $uri $uri/ /index.php?$query_string;
```

---

# Development Notes

- Source code is mounted into containers using Docker volumes for live development.
- MySQL data is persisted using Docker named volumes.
- Composer and npm run inside the app container.
- PHP execution is handled by PHP-FPM.

---

