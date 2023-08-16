---
title: "How incident drills help us prepare for the inevitable"
date: 2023-02-28T11:30:50+01:00
summary: "Even with the best engineering, incidents do happen. We have therefore started running regular incident drills to test our response readiness and train ourselves to be better prepared for the next incident. This also helps us to try out new incident response procedures, without having to wait for an actual incident to happen."
draft: false
canonicalUrl: https://blog.funda.nl/how-incident-drills-help-us-prepare-for-the-inevitable/
---

At funda we strive to build software which scales and performs well. We could assume nothing will ever go wrong and therefore we wouldn't have to worry about outages. But David Soff, Site Reliability Engineer at funda, would not be writing this post if we did that.
Even with the best engineering, incidents do happen. We have therefore started running regular incident drills to test our response readiness and train ourselves to be better prepared for the next incident. This also helps us to try out new incident response procedures, without having to wait for an actual incident to happen.

## What are incident drills?

An incident drill is a simulated incident to which the participants need to respond. Each drill focuses on an aspect of incident response. Examples of these are:

- Communication
- Systems Knowledge
- Knowledge of procedures
- Debugging

It is up to the Drill Master to decide if the participants know what the training goal is. This way, a drill can be used for skill assessments and a form of deliberate practice.

## Who runs the incident drills?

At this point we only run incident drills within the Site Reliability Engineering team.

During the drill there are two groups of people:

- Drill Master (DM): They prepare the drill, decide on the training goal and have absolute control over the events during the drill. They are the eyes and ears of the responders. They control every aspect of the world the responders live in during the drill.
- Responder: Responders respond to the incident. We always assign one responder as the on-call engineer. They will be the first to receive an alert and will therefore be the initial Incident Commander.

We have found that having one DM per three responders is an acceptable ratio in our current setup. This is because a DM needs to respond to all queries and actions taken by the responders. If there are more than three responders, the DM easily gets overwhelmed.

Our incident response procedure and roles are heavily influenced by the PagerDuty Incident Response Procedures. PagerDuty keep the documentation up to date and even have a section dedicated to some anti-patterns during incident response. If you’re reading this article looking to improve your incident response, I would highly recommend also reading through the PagerDuty documentation and seeing if there are any learnings from there you can try out during your next incident drill.

## How do we run incident drills?

Well for that we will discuss what happens before the drill, during the drill and after the drill. 

### Before the drill

We try to keep it simple. The DMs prepare a scenario which includes: the trigger, initial symptoms, supporting data the participants may ask about, what participants need to do to resolve the incident, and the root cause.
For extra spice they can also prepare a couple of curveballs they can throw at any moment. Examples of these are:

- A responder loses internet connectivity
- An unrelated incident is triggered
- The CEO notices and starts asking for updates every 5 minutes
- Someone needs to use the bathroom

### During the drill

The participants can ask questions of the drill master through direct messages. This is to simulate the participants going into the monitoring systems on their own laptops. It also forces them to communicate any findings they have as if they were responding to a real incident.
It is up to the DM to respond to unanticipated questions. This means they need a thorough understanding of the incident and its consequences. We have found that this also helps a lot with knowledge sharing.

### After the drill

After the drill, we run a mini ‘post-mortem’ as if we had responded to an actual incident. This ensures that we review our response in the same way as an actual incident. As our drills focus on incident response and not on incident prevention, this post-mortem is focused on the timeline, and not on how to fix any technical issues or on establishing the root cause.
Once the post-mortem is done, we review the drill itself. This means we can improve it for the next time we run this specific drill, and we get some general improvements for future drill preparations. 
For example, during our most recent drill we ran into an issue where a fictitious service was named in a deceptive way, causing the DM to have to give some hints as to where to look. During the review, we discussed this and updated the drill instructions so that the name is more descriptive of the service. This will make future runs of this drill more realistic so we can focus on the training goal of the drill.
Finally, we decide on when the next drill is, and who will be the DM.

## Where do we run incident drills?

We only run incident drills in person. We feel this helps us give faster feedback when doing the post-action review. However, since our incident response procedure does not involve us having to travel to the same location, there is nothing about the incident drill itself which forces it to be run in person.

## When do we run incident drills?

Within the Site Reliability Engineering team, we try to run an incident drill at least 6 times per year.
This gives us enough time to apply the improvements discovered during the most recent drill, and for the next DMs to find the next weak point and prepare a drill to address it.

## What have we learned so far?

So far we have learned that our communication during an incident needs to be clear and concise. One of the things we noticed is that we tended to only communicate verbally. This is nice when you’re throwing around hypotheses, but it makes it really hard to keep track of who is working on which hypothesis, what facts they have found, and if they are taking any action.
By keeping a log of these things in some written form, it makes it easier for people joining at a later stage to figure out what the facts are and what is already being looked into. It also helps a lot when reconstructing the timeline during the post-mortem since written communication is (usually) time-stamped.
A second lesson for us was that when there are three or more people working on an outage you really need to have one incident commander who approves all actions taken, prioritizes which hypotheses need to be looked into, and who delegates these tasks when needed.

## What's next?

We have plans to start running drills with some interested colleagues outside of Site Reliability Engineering. We hope this will help us write better operational procedures for our services. Finally, we hope to be using these drills to get our new Site Reliability Engineering colleagues ready for on-call shifts faster and in a more fun way.