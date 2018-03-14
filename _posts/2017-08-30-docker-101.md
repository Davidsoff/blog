---
layout: presentation
title: Docker 101
theme: black
transition: slide
---
<section data-markdown>
## Docker 101
By David Soff
</section>

<section data-markdown>
## Before I start:
please clone https://github.com/Davidsoff/docker101 for the hands-on part
</section>

<section data-markdown>
## What is Docker?
- Lightweight containers
- Only share the kernel of the host
- Smaller and quicker to start than VMs
- typically only runs a single proccess

</section>

<section data-markdown>
## Docker vs VM
 ![vs vm](/images/docker-vm-container.png)
</section>

<section data-markdown>
## Architecture
 ![architecture](/images/architecture.svg)
</section>

<section data-markdown>
## How to use Docker?
 Download it from [docker.com](https://www.docker.com/community-edition)
</section>

<section data-markdown>
## building images pt. 1
create a build description in a Dockerfile
</section>

<section data-markdown>
## building images pt. 2
```bash
$ docker build -t my-image .
```
</section>

<section data-markdown>
## running images
```bash
$ docker run --name my-container -p 8080:80 my-image
```
</section>

<section data-markdown>
## viewing containers
```bash
$ docker ps
```
</section>

<section data-markdown>
## stopping images
```bash
$ docker kill my-container
```
</section>

<section data-markdown>
## Hands-on time!
</section>

<section data-markdown>
## Static application
simple serving of html files
</section>

<section data-markdown>
## Dynamic application
simple customised Hello World spring boot application
</section>

<section data-markdown>
## Multi container setups

- Applications need storage
- One process per container

</section>

<section data-markdown>
## Docker Compose

- lightweight container orchestration

</section>

<section data-markdown>
## Multistage builds

- New feature in Docker 17.05
- Separates build environment and runtime environment
- Optimised containers for each role
- Allows for very small containers

</section>

<section data-markdown>
## Questions?
</section>

<section data-markdown>
## Thank you!
</section>
