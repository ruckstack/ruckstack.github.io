---
title: Ruckstack Server Overview
permalink: /docs/server/
layout: single
sidebar:
    nav: "docs"
---

The output of the [ruckstack build](/docs/cli) process is an installable version of your entire stack.

### How Does It Work?

At its core, the packaged server is a [k3s-based](http://k3s.io) Kubernetes instance that is configured and optimized for a a single application, on a small (1 to 5) machine cluster.

The Kubernetes system is in charge of making sure all the pieces of the infrastructure are running and working as well.

Around this Kubernetes core, is a custom management layer to simplify the operation of the server.

### What About Your Code?

Your application runs within the Kubernetes environment. 

Because your application is packaged as containerd images, it runs in an isolated and consistent sandbox. 
It does not matter what is installed (or not installed) on the host system--your application always runs in exactly the environment you need.

Kubernetes also abstracts away all the network configuration, so no matter what the underlying network configuration is, your services can talk to each other in a standard way.

Finally, Kubernetes watches the health of the system, and if it sees services no longer responding, it will automatically restart them for you.    

  