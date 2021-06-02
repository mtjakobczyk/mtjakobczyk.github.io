Welcome to [mtjakobczyk's](https://github.com/mtjakobczyk) personal GitHub page.

### Self-hosted Kubernetes
Inspired by one of the finest and famous (and Google-oriented) tutorials ([Kubernetes - The Hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way)), I compiled a smaller-in-size set of instructions for multiple environments. On this page you can find a set of instructions how to architect a self-hosted Kubernetes cluster on different infrastructures. I will focus here on the platform only (runtime). A complete and useable environment will still require application-lifecycle processes and tools (such as CICD).

> **Disclaimer:**<br/>in most cases you **should always** consider using **managed Kubernetes** (such as GKE, EKS, AKS or OKE) first, unless you have good reasons, sufficient DevOps manpower and an involved Security team. Self-hosted Kubernetes is hard, comes with huge responsibility and often costs a lot of "operations money". 

If your intention is to set up a production cluster, these instructions may be inspiring, but are surely insufficient. Remember this.

Let's start. In the first stage we need: 
1. a few initial architectural decisions, 
2. infrastructure (nodes and networking), 
3. a set of certificates for Kubernetes components

#### 1. Architecture (initial decisions)
I am going to use a "frontline architecture" approach. We will initially focus on the most important decisions required to properly scope the cluster and kick-off the action fast.

Look at this checklist:
1. What will be the nature of the workload (*network-intensive stateless APIs* or *disk-intensive computational jobs*)?
2. Are we going to host *a single distributed system with many components* or *multiple systems that require very strict isolation* in one Kubernetes cluster?
3. Do we plan any stateful components to run inside the cluster (such as a database engine)? Is it possible to avoid it?
4. How many CPUs and memory do we want to offer for containers in the beginning?
5. Do we expect rather *stable load* or we need to be able *to scale the resources* (CPUs, memory)?
6. Are we going to rely on the infrastructure in public cloud or on-premises (private cloud, hypervisor-controlled VMs, physical hardware, ... IoT devices)?

This list seems ridiculously short, but believe me or not, it will work. Stuff like users, ingress, installation method, observability is important, but will come a bit later. 


