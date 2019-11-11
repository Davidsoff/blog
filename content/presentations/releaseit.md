---
title: "Release it!"
date: 2019-11-01T15:42:04+01:00
draft: true
summary: A talk about building software that can survive production.
---
layout: true

class: center, middle

---

# Release it!

## Production ready systems

By: David Soff

@SoffDavid

---

# Software is only useful in production.

But most software is not necceseraly written with production in mind.

---

# Does passing QA mean being ready for production?

---

# What will the software look like in three to ten years?

---

# Failure is expensive.

???

If a minute of downtime costs one million euros, and a deployment means 1 minute of downtime.
It would be a nobrainer to invest half a million euros to build a zero downtime deployment.
Even if you only deploy once every quarter, it would pay itself back within one -and-a-half months.

---

# Descisions, descisions, descisions.

Earlier == harder to change

---

# The future is unpredictable and plans are bound to change

Therefore: design for change

---

# The bug that brought down an airline

A bug in the Oracle database driver caused the check-in kiosks to stop working
This bug made it so that connections to the database where not correctly closed after a failover.
This in turn caused the kiosk servers to run out of resources
A reboot of the affected applications fixed the problems

---

# So how to prevent the next outage?

Testing is easy once you know what to look for

> Bugs cannot be eliminated, so they must be survived instead.
> .origin[Michael T. Nygard]

---

# Goal

## Prevent bugs from causing a chain of failures.

---
layout: true
class: left, middle

---

# Defining Stability

- **Transaction**: Abstract unit of work processed by the system.
- **System**: Everything needed to process a transaction.
- **Impulse**: A rapid shock to the system.
- **Stress**: A force applied to the system over a longer period of time.
- **Strain**: A change in the "shape" of the system caused by stress.

---

layout: true
class: center, middle
s
---

# Both *Impulses* and *Stress* can cause excessive *Strain*

---

[[insert glas shattering and metal fatigue gifs here]]