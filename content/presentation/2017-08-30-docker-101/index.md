---
title: Docker 101
date: 2017-08-30T16:12:32+01:00
summary: An introductory look at Docker
slug: "2017-08-30-docker-101"
draft: false
---

layout: true

class: center, middle

---

## Docker 101

By David Soff

---

## Before I start

please clone <https://github.com/Davidsoff/docker101> for the hands-on part

---

## What is Docker?

- Lightweight containers
- Only share the kernel of the host
- Smaller and quicker to start than VMs
- typically only runs a single proccess

---

## Docker vs VM

 ![vs vm](docker-vm-container.png)

---

## Architecture

 ![architecture](architecture.svg)

---

## How to use Docker?

 Download it from [docker.com](https://www.docker.com/get-started/)

---

## Anatomy of a Dockerfile

Dockerfile is built in layers

Every line in the file is a layer that has a unique hash.

This means layers can be reused between builds.

---

## A simple Dockerfile

```Dockerfile
FROM nginx:alpine

COPY html /usr/share/nginx/html

EXPOSE 80
```

---

## Building images

```bash
docker build -t my-image .
```

???

docker build looks for Dockerfile in the context directory by default

---

## running images

```bash
docker run --name my-container -p 8080:80 my-image
```

---

## viewing containers

```bash
docker ps
```

---

## stopping images

```bash
docker kill my-container
```

---

## Hands-on time

---

## Static application

simple serving of html files

```Dockerfile
FROM nginx:alpine

COPY html /usr/share/nginx/html

EXPOSE 80
```

`docker build -t static .`

`docker run -p 3000:80 static`

---

## Dynamic application

simple customised Hello World spring boot application

```Dockerfile
FROM gradle:alpine

ADD awesome_application .

RUN gradle build

ENV JAVA_OPTS=""

EXPOSE 8080

ENTRYPOINT exec java $JAVA_OPTS -jar build/libs/app.jar
```

???

`docker build -t dynamic .`

`docker run -p8080:8080 dynamic `

---

## Container orchestration

- Docker compose
    Lightweight container orchestration, Excelent for local development
- Kubernetes
    Production grade container orchestration.

---

## Multi container setup

- Applications need storage
- One process per container

## Docker compose configuration

### **`compose.yaml`**

```yaml
version: '3'

services:
  application:
    build: .
    ports:
      - "4001:4000"
    depends_on:
      - postgres

  postgres:
    image: "postgres:alpine"
    environment:
      - POSTGRES_PASSWORD=postgres
      - POSTGRES_USER=postgres
      - POSTGRES_DB=multi_container_application_dev
```

`docker compose up --build`

`docker compose down`
---

## Multistage builds

- Separates build environment and runtime environment
- Optimised containers for each role
- Allows for very small containers

## Multistage example

```Dockerfile
FROM gradle:alpine AS builder

ADD awesome_application .
RUN gradle build

FROM openjdk:jre-alpine

ENV JAVA_OPTS=""
COPY --from=builder /home/gradle/build/libs/app.jar /app/app.jar

EXPOSE 8080

ENTRYPOINT exec java $JAVA_OPTS -jar /app/app.jar
```

???

`docker build -t multistage .`

`docker run -p8080:8080 multistage`

---

## Questions?

---

## Thank you
