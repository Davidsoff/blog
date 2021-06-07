---
title: Docker 101
date: 2017-08-30T16:12:32+01:00
summary: An introductory look at Docker
---

layout: true

class: center, middle

---

## Docker 101

By David Soff

---

## Before I start:

please clone https://github.com/Davidsoff/docker101 for the hands-on part

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

 Download it from [docker.com](https://www.docker.com/community-edition)

---

## building images pt. 1

create a build description in a Dockerfile

---

## building images pt. 2

```bash
$ docker build -t my-image .
```

---

## running images

```bash
$ docker run --name my-container -p 8080:80 my-image
```

---

## viewing containers

```bash
$ docker ps
```

---

## stopping images

```bash
$ docker kill my-container
```

---

## Hands-on time!

---

## Static application
simple serving of html files

---

## Dynamic application
simple customised Hello World spring boot application

---

## Multi container setups

- Applications need storage
- One process per container

---

## Docker Compose

- lightweight container orchestration

---

## Multistage builds

- New feature in Docker 17.05
- Separates build environment and runtime environment
- Optimised containers for each role
- Allows for very small containers

---

## Questions?

---

## Thank you!
