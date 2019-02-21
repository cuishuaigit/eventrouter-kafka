# Eventrouter

This repository contains a simple event router for the [Kubernetes][kubernetes] project. The event router serves as an active watcher of _event_ resource in the kubernetes system, which takes those events and _pushes_ them to a user specified _sink_.  This is useful for a number of different purposes, but most notably long term behavioral analysis of your 
workloads running on your kubernetes cluster. 

## Goals

This project has several objectives, which include: 

* Persist events for longer period of time to allow for system debugging
* Allows operators to forward events to other system(s) for archiving/ML/introspection/etc. 
* It should be relatively low overhead
* Support for multiple _sinks_ should be configurable

### NOTE:

There is  a default image: fastop/eventrouter:kafka, use my kafka-cluster[K8s-kafka][k8s-kafka], you can build yourself image and use yours kafka
cluster.

just vist interface.go.

## Running Eventrouter 

Clone code:
```
$git clone https://github.com/cuishuaigit/eventrouter-kafka.git
```
Standup: 
```
$ kubectl create -f eventrouter-kafka/yaml/eventrouter.yaml
```
Teardown: 
```
$ kubectl delete -f eventrouter-kafka/yaml/eventrouter.yaml
```

### Inspecting the output 
```
$ kubectl logs -f deployment/eventrouter -n kube-system 
``` 

Watch events roll through the system and hopefully stream into your ES cluster for mining, Hooray!

[kubernetes]: https://github.com/kubernetes/kubernetes/ "Kubernetes"
[k8s-kafka]: https://github.com/cuishuaigit/k8s-kafka "K8s-kafka"
