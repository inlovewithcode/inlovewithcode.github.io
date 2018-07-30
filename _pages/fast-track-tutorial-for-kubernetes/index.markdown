---
author: guidedmissile
comments: false
date: 2018-02-19 11:19:49+00:00
excerpt: 'Covers keywords and their meaning/purpose related Kubernetes.


  Keywords: Pods, Containers, Replica Sets, Service, Job, Deployment, Rollout, Config
  Maps, Secrets, Persistent Volumes, Resource Management.'
layout: page
link: https://inlovewithcode.wordpress.com/
slug: fast-track-tutorial-for-kubernetes
title: Fast track tutorial for Kubernetes learning(actually for lazy/impatients :)
wordpress_id: 2597
---

# Kubernetes

Keywords: Pods, Containers, Replica Sets, Service, Job, Deployment, Rollout, Config Maps, Secrets, Persistent Volumes, Resource Management.

_Note: This page is only intended to only provide you a quick understanding of terminology and their meanings and not to be considered as a complete overview of its architecture or design._

Source: https://docs.kubernetic.com/


## Pods

  * Container is a process (or set of processes) that runs in a jailed environment so that it doesn't interfere with other processes. This means from the point of view of the application (process) it has its own IP, disk, cpu, and memory.

  * A Pod is an instance of one or more containers under the same IP. In most cases a Pod contains just one container, in some edge cases a pod contains multiple containers and they are bound by the same IP to create a tight integration.

  * Containers inside the same Pod are co-located (tight-coupling**) (they cannot be spread to different machines), the scale up or down together (they cannot be scaled separately if needed) and share the same network IP (There may exist port conflicts if not designed properly).



## Replica Sets


  * A Replica Set defines the Pods that needs to run and the number of their replicas.
Advantage - without breaking above tight-coupling**, we improve


## Deployment



  * The objective of Deployment is to manage an upgrade or downgrade of a service without having downtime during the upgrade we have to handle multiple instances of both versions during the upgrade.



  * There are both `Deployment` and `Rollback Deployment` available






## Job



  * A job creates one or more pods and ensures that a specified number of them successfully terminate.



Example: run 10 jobs but only 3 in parallel at a time



## Services




  * A Service is basically a group of Pods that constitute a Service (e.g. a group of Nginx instances). When someone wants to access this group of Pods it does it through the service, which will redirect the request to one of those Pods.



## Service Account



  * A service account provides an identity for processes that run in a Pod.



## Config Maps



  * The ConfigMap API resource holds key-value pairs of configuration data that can be consumed in pods or used to store configuration data for system components such as controllers.



## Secrets



  * Objects of type secret are intended to hold sensitive information, such as passwords, OAuth tokens, and ssh keys





## Persistent Vol

  * Persistent Volumes define where Pods can claim Storage for their instances.

## Resource Quotas

  * Resource quotas are a tool for administrators to ensure fair share of resources. Cluter level.

## Limit Ranges


  * Limit Ranges helps define boundaries on the memory and cpu that Pods can claim on each namespace. This helps cluster operators manage the resources efficiently.


# Kubernetes best practice

>    by Sandeep Dinesh (google)

Why? Flexibility creates diversity => diversity can be dis-organised and dis -oriented at times


* Don't trust arbitary base images!
* Use small base images
     * Builds faster
     * needs less storage
     * cold start are fasters
     * potentially less attack surface - as less no.of packages
* ** Builder Pattern **

  Code
    -> Build Containter [compiler / dev deps/uni tests/..]
      -> Build Artifacts(s)[binaries/static files/bundles/transpiled code]
        -> Runtime Env [Debug/Monotor Tooling]
  
* Use a non-root inside a container
* Kubernetes can enforce use `runAsNonRoot` & `readOnlyRootFilesystem` # Just adding extra security layers
* One process per container/pod
* Dont restart on failure. Crash cleanly instead.
* Log to stdout & stderr. It goes to stackdriving.

## Deployments

* Use the `record` for easy roll back; for production deployments

        kubectl apply -f deployment.yaml --record

* use plenty of descriptive labels
* use sidecar containers for proxies, watchers, etc
* dont use sidecars for bootstrapping
    * use init container. for one time jobs.
* dont use `latest` or `no tag`: prefer a git hash
* readiness and liveness probes are your friend
    * Kube says that just process is runnng and not running # no so good.
    * prefer setting Readiness and Liveness.
    * Readiness - required for production app

## Servies

* Dont always use type : LoadBalancer
    * Ingress is great. use it. becoz - it can work on multiple load balencing with one single point.
* type: NodePort can be `good enough`

* Use statics IPs. They are free ! 
* Mapping external sericves to internal services


* User Helm Charts
* be ready for ` all downstream dependencies are un relioable`
* use `service mesh` - linkerd/linker & istio/istio - docker for micro-service management
* make micro-services are not too micro
* PaaS ? DEIS/ OPENSHIFT/KEL


* Use Container Engine
* Resources, Anti-affinity, node-affinity
* node taints/tolerations (special hw) (dedicated hosts) etc
* affinity/anti-affinity (hostname/zone/region)
* Use Namespaces to split up your cluster

* Role Based Access Control
* Unlesash the chaos monkey - randomly - delete pods to check the worst case scenario


