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





## Persistent Volumes







  * Persistent Volumes define where Pods can claim Storage for their instances.





## Resource Quotas







  * Resource quotas are a tool for administrators to ensure fair share of resources. Cluter level.





## Limit Ranges







  * Limit Ranges helps define boundaries on the memory and cpu that Pods can claim on each namespace. This helps cluster operators manage the resources efficiently.


