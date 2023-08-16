---
title: "Why GitOps didn’t work for us as a company"
date: 2022-05-03T11:30:50+01:00
summary: "Why GitOps didn’t work for us as a company"
draft: false
canonicalUrl: https://blog.funda.nl/why-gitops-didnt-work-for-us-as-a-company/
---

## How it started

Two years ago, I presented GitOps to our team. At that time, we were about to switch from DC/OS Marathon to Kubernetes. For us this meant a big change in the way we were running our containers. Kubernetes brought the promise of native autoscaling, rolling deploys, and many other exciting possibilities. To manage these big changes, we needed to rethink our deployment strategy. Up to this point we were using an Ansible script and a Python script to achieve 'zero downtime deploys'.

We quickly agreed that we would like to minimize the possibility of configuration drift. At this point we’d done some work with Terraform and we liked how it was able to show us the changes it was going to make to our infrastructure. However, we weren't keen on the fact that we would have to trigger a Terraform cycle to detect any configuration drift that might have happened.

And that is why we turned our attention to GitOps, and more specifically Flux (a GitOps implementation by WeaveWorks).

## What is GitOps?

The Idea behind GitOps is to have your desired Kubernetes state in version control. Someone known as a GitOps Operator then checks this version control for any changes and makes the necessary changes so that the actual state matches the desired one. Because all changes have to be committed to version control, this has the added benefit of giving you a complete audit log.

Besides the traceability this gives during incident response, the attack surface of your cluster is also greatly reduced, since credentials with write permission are only accessible within the cluster. These benefits convinced the Site Reliability Engineering (SRE) team to start using Flux to manage our Kubernetes clusters.

## Starting the implementation

Developers at funda were used to actively pushing changes to a cluster. They built their application and then deployed their changes by running a deployment pipeline. Effectively they ‘pushed’ their new version to whatever environment they were supposed to use during that stage of the development lifecycle.

Using Flux completely inverted this way of working. In our case it meant that in order to deploy some code on a feature branch, a developer would have to make a change on a different branch than the one they were currently working on. We tried to avoid this by creating a script that would do it automatically as part of a ‘deployment’. This script would then force a reconciliation cycle. This created the illusion that developers were still pushing changes to the cluster, while in reality the cluster was actually pulling in their changes.

## The downside

This script was very limited in terms of the changes it would allow. This meant that any unsupported changes, like scale and CPU requests, would need to be carefully merged into the main branch to avoid breaking other environments. This leaky abstraction caused quite a lot of frustration and friction with our developers. The mismatch between simple container image updates being pushed and all other Kubernetes changes needing to be merged also broke the workflow of many teams. They now had to make a pull request, get that approved and then wait for the change to propagate to their environment just to test a small change to their Kubernetes configuration. This extra work reviewing pull requests caused a significant loss in development speed and made it significantly harder to make small changes.

## What have we learned from this?

Currently, we are slowly moving our applications back to a completely push-based workflow. Within the SRE team we are still evaluating if we want to keep using Flux for changes that are shared by the whole cluster like monitoring agents, Azure integrations, and networking. The developers are slowly being migrated away from the pull-based flow, thereby removing the number of moving parts they need to be aware of.

Does this mean we will never use GitOps in the future? No, most definitely not. We will however be a lot more careful in the rollout and adoption of a future implementation. During the process we discovered that we didn’t pay enough attention to our developers and that we tried to hide the changes behind a (very) leaky interface.

## Could GitOps work for you?

Had we taken the time to sit with our development teams, we might have been able to spot the issues with using GitOps in combination with a Gitflow workflow. In future I would only recommend adopting GitOps for global cluster setup, or for applications being developed with a centralized workflow. These two situations have a branching structure, which tends to map fairly easily to having multiple clusters.

For us, implementing GitOps was quite an adventure, with lots of highs but also some lows. I suspect we will be revisiting the subject again at some point in the future, but for now we are quite happy to be going back to our tried and tested push deploys.