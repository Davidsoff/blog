---
title: "Kubernetes Best Practices"
date: 2020-01-20T11:30:50+01:00
summary: "Kubernetes Best Practices"
---

## Basic service knowledge

- Don't use latest in your image definitions, it will be mutated on every push to the repo. this makes it hard to figure out what version of the code is running.
- Preferably tag all images with the git hash used to build the image. This makes it easy to find the exact commit used to deploy.
- Keep in mind taht changing a secret or a config map will not automatically reload/redeploy/restart your application to use it.
- Secrets are not encrypted by default, you will need to integrate with a key provider for Kubernetes to do this.
- Deployments can be used to create rolling deploys and ensure all instances are created equally.
- Do keep parametrization in mind. This can be done with packaging tools like helm.

## Developer workflows

There are multiple phases to building out development clusters:

### Onboarding

get users set up to use the dev cluster,

### Developing

### Testing
  