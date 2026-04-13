---
categories:
  - Tecnologia
date: 2026-04-13T00:00:00+02:00
lastmod: 2026-04-13T00:00:00+02:00
description: 'How I built a production ready Docker image for Sendy, the self-hosted newsletter app, to replace a repetitive manual installation process: now listed as a community contribution on the official Sendy integrations page.'
draft: false
keywords:
  - Docker
  - Sendy
  - Open Source
  - DevOps
tags:
  - Docker
  - Sendy
  - Open Source
title: 'Running Sendy with Docker'
url: '/running-sendy-with-docker'
type: post
image: "https://images.unsplash.com/photo-1584438784894-089d6a62b8fa?q=80&w=2000&auto=format&fit=crop"
---

# Running Sendy with Docker

## What is Sendy?

[Sendy](https://sendy.co) is a self-hosted email newsletter application that sends emails through Amazon SES.
The pitch is simple: instead of paying a growing monthly fee to services like Mailchimp, you pay $$$ once for the software and $1 per 10,000 emails to Amazon. That's it.

The installation involves some zip unpacking, point it at a database, configure some directories, license and you're running your own newsletter platform.

## The problem: manual and repetitive

Sendy's installation guide is straightforward if you are comfortable with FTP and MySQL. However, every time I needed to set up a new instance: a new server, a fresh environment, a test deployment or upgrade between versions, I had to go through the same steps again. Configure Apache, set up PHP with the right extensions, create the database, copy files, edit the config. It worked, but it was the kind of repetitive work that eventually motivates you to automate it.

So I did.

## The Docker image

I invested some time building a production ready Docker image for Sendy, available at [marcelorodrigo/sendy](https://github.com/marcelorodrigo/sendy) on Docker Hub.

Some decisions I made along the way that I'm happy with:

- **Based on [ServerSideUp/PHP](https://github.com/serversideup/docker-php)**: a well-maintained Apache/PHP base image with s6-overlay for process supervision
- **PHP 8.5 with opcache** tuned for production
- **Non-root user**: the container does not run as root
- **Multi-architecture**: native `amd64` and `arm64` images, so it runs on Apple Silicon and standard x86 servers alike
- **CloudFlare support**: real client IP addresses are passed through correctly from trusted proxies
- **All logs to STDOUT/STDERR**: plays well with any centralized logging setup
- **Health check**: built in container orchestrators can detect when the app is ready

Required PHP extensions are pre-installed and `mod_rewrite` is enabled, so Sendy works out of the box without any manual tuning.

## Quick start

If you already have a MySQL database, you can run Sendy with a single command:

```bash
docker run -d \
  -e SENDY_URL=https://newsletters.example.com \
  -e MYSQL_HOST=db.example.com \
  -e MYSQL_USER=sendy \
  -e MYSQL_PASSWORD=your_password \
  -e MYSQL_DATABASE=sendy \
  -v sendy_uploads:/var/www/html/uploads \
  -p 80:8080 \
  marcelorodrigo/sendy:latest
```

`SENDY_URL`, `MYSQL_USER`, and `MYSQL_PASSWORD` are the only required variables. The image validates them on startup and refuses to start if they're missing — a small quality-of-life touch that prevents silent misconfiguration.

## Full setup with Docker Compose

For a complete local or self-hosted setup, here's a working `docker-compose.yml` that also spins up MySQL:

```yaml
services:
  sendy:
    image: marcelorodrigo/sendy:latest
    ports:
      - "80:8080"
      - "443:8443"
    environment:
      SENDY_URL: "https://newsletters.example.com"
      MYSQL_HOST: "mysql"
      MYSQL_USER: "sendy"
      MYSQL_PASSWORD: "Pl3ase_Ch8nge_Me"
      MYSQL_DATABASE: "sendy"
    volumes:
      - sendy_uploads:/var/www/html/uploads
    depends_on:
      - mysql

  mysql:
    image: mysql:8.4
    environment:
      MYSQL_ROOT_PASSWORD: ThisIsAS7rongR00tPassw0rd
      MYSQL_DATABASE: sendy
      MYSQL_USER: sendy
      MYSQL_PASSWORD: Pl3ase_Ch8nge_Me
    volumes:
      - mysql_data:/var/lib/mysql

volumes:
  sendy_uploads:
  mysql_data:
```

Run `docker compose up -d`, open your browser, and Sendy's installer will greet you. The whole process takes a couple of minutes instead of an afternoon.

## Community recognition

The best part came after publishing the image: it is now listed on the [official Sendy integrations page](https://sendy.co/api) as a **Community maintained Docker image**. A small but satisfying milestone for a project that started purely as a way to stop repeating myself.

If you use Sendy and want to run it in Docker, give it a try. Feedback and contributions are welcome on [GitHub](https://github.com/marcelorodrigo/sendy).
