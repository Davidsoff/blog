---
title: "Machine Learning Best Practises"
date: 2020-01-16T14:46:37+01:00
draft: true
---

Assuming you have your cool new machine learned model, you will probably be wanting to show it off to your friends.
This post will lay out a couple of best practises around hosting and running your machine learned models
<!--more-->

## Deploying

To deploy your model you will have to export it, there are multiple file types available for this so pick the one your programming language supports.

For python some common file formats are: 

- Pickle
- joblib

It is also possible to export models trained using tensorflow to a tensorflow specific file format.
Tensorflow is also supported by R

### Serving

There are many solutions for serving a model. Most solutions do follow the principle of exposing an api and converting the request data to the format expected by the model. Some frameworks have more built in features so less code is needed to get an application which can serve predictions.

## Retraining

Your first model was trained using a training set. This training set is a snapshot of the world (or the piece you are evaluating atleast) at a specific moment in time. Since change is inevitable, your trainingdata will become outdated and will need to be refreshed. This also means your model is out of date. This phenomenon is called _model drift_.

There are multiple ways of detecting model drift and there is no one-size-fits all, a few ways of checking for model drift are:

- Examining the feature distributions of training and live data
- Examining the correlations between features
- Examining the target distributions

A more thorough explanation on what this means can be found [here](https://mlinproduction.com/model-retraining/)

## Monitoring

Once your model is in production you will want to keet rack of the folowing metrics next to your normal monitoring of CPU, memory, latency, throughput, etc

### Age of the model

The model will become less accurate if you do not retrain it regularly using fresh data

### Accuracy of the model

Keep tabs on the accuracy of the model so that you can detect sudden changes. Big changes may be an indication of a problem.
Also remember to validate your accuracy using human feedback.

### Output distribution

Keep tabs on the distribution of your predictions. Sudden changes in the distribution can be an indication of bugs or problems. 
Although this can also be caused by changes in the input conditions, it is certainly worth investigating the cause of the sudden change.


## Sources

[https://blog.dominodatalab.com/on-being-model-driven-metrics-and-monitoring/](https://blog.dominodatalab.com/on-being-model-driven-metrics-and-monitoring/)
[https://mlinproduction.com/model-retraining/](https://mlinproduction.com/model-retraining/)
