Welcome to [mtjakobczyk's](https://github.com/mtjakobczyk) personal GitHub page.

### Kubernetes Setup
Inspired by one of the finest and famous (and Google-oriented) tutorials ([Kubernetes - The Hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way)), I compiled a smaller-in-size set of instructions for multiple environments. On this page you can find a set of instructions how to architect a self-hosted Kubernetes cluster on different infrastructures.

#### Planning
I will focus here on the platform only (runtime). A complete and useable environment will still require application-lifecycle processes and tools (such as CICD).

> In this cookbook I am mixing planning and doing.<br/> Do not base on my instructions, if your intention is to set up a production cluster. ;)

To start, we need: 
1. architecture (the expected target picture), 
2. infrastructure (nodes and networking), 
3. a set of certificates for Kubernetes components

My "frontline architecture" checklist:
1. How many CPUs and memory do we want to offer for containers in the beginning?
2. Do we expect stable load or we need to be able to scale the resources (CPUs, memory)?
3. Are we going to rely on the infrastructure in public cloud or on-premises (private cloud, hypervisor-controlled VMs, physical hardware, ... IoT devices)?
4. Are we going to host *a single distributed system with many components* or *multiple systems that require very strict isolation* in one Kubernetes cluster?
5. What will be the nature of the workload (network-intensive stateless APIs or disk-intensive computational jobs)?

This list seems ridiculously short, but believe me or not, using this "frontline architecture" approach, stuff like users, ingress, installation method can be planned a bit later.

> One important thing: <br/>in most cases you **should always** consider using **managed Kubernetes** first, unless you have a reliable and strong DevOps manpower. Self-hosted Kubernetes is hard, comes with huge responsibility and costs "operations money". 
