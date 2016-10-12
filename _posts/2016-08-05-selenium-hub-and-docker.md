---
layout: post
title:  "Selenium grid and docker"
date:   2016-08-05 10:20:00 +0200
categories: software tools automation
author: David
comments: true
---

Selenium grid allows you to run tests against multiple browsers on potentially different machines.
This is especially usefull when there is a need to parallelise the running of automated browser tests.

This is a sample file which can be used to create a hub with a single connected chrome agent.
The compose file assumes you have you application runnin inside docker and that you have given it a network. 
I haven't tried linking the grid to applications not running in docker but I suspect this must be doable with some fidling.

{% highlight YAML %}
version: '2'
services:
  hub:
    container_name: hub
    image: selenium/hub
    environment:
      - GRID_BROWSER_TIMEOUT=100000
      - GRID_TIMEOUT=90000
    ports:
      - '4444:4444'
    networks:
      selenium-network:
        aliases:
          - hub
  chrome:
    image: selenium/node-chrome
    links:
      - "hub:hub"
    external_links:
      - <application-to-test>
    depends_on:
      - hub
    environment:
     - HUB_PORT_4444_TCP_ADDR=hub
      -HUB_PORT_4444_TCP_PORT=4444
    networks:
      - selenium-network
      - <network-of-application-to-test>
networks:
  selenium-network:
    driver: bridge
  <network-of-application-to-test>
    driver: external
{% endhighlight %}

To start the hub use:
{% highlight bash %}
docker-compose up -d
{% endhighlight %}

After the containers have started you can scale the amount of nodes like so:
{% highlight bash %}
docker-compose scale chrome=5
{% endhighlight %}
In that example chrome was scaled to five nodes but it can just as easily be scaled to 10 or 20 nodes.
