---
title: "Intro to DC/OS"
date: 2019-11-21T10:43:45+01:00
summary: "An introduction to DC/OS, mesos, marathon and metronome."
draft: true
---

DC/OS is a product by D2IQ (formerly Mesosphere). It is based on [Apache Mesos](http://mesos.apache.org/).
Mesos is a resource manager, this means that it exposes the resources in a cluster to be requested by different frameworks through an HTTP API.
Mesos uses [Apache Zookeeper](https://zookeeper.apache.org/) for cluster state management and leader election.
For long running services DC/OS uses the [Marathon](https://mesosphere.github.io/marathon/) framework.
For one-off jobs and scheduled tasks, DC/OS uses the [Metronome](https://docs.d2iq.com/mesosphere/dcos/1.13/deploying-jobs/) framework.

So if you want to run a service untill you deploy a new version or stop the service, you will use Marathon.

If you want to run a one of job or a scheduled task, like an integration test, you will use Metronome.

## Deploying

Deploying a marathon service, or metronome job is done by POSTing a json file to the correct endpoint.
The mesos framework will then request enough resources from mesos to run the task. If mesos has the resources it will
