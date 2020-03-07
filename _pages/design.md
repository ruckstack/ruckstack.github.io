---
title: Requirements & Design
permalink: /design
---

Kubernetes is an amazingly complex and flexible system. There are always many ways to do the same thing, and many different scales it is able to work at.
Ruckstack's requirements are very different than more Kubernetes systems you see. 

### We need a system that:

- Is installed on a handful of servers (1 to 10), not thousands
- Runs one application, not thousands
- Is managed by admins who are not Kubernetes experts
- Has applications written by developers who are not Kubernetes experts
- Installation must be dead-simple because it is not managed by standard Ansible jobs
- Does not depend on network access to automated dependency downloads
- Looks and feels like a "normal" installed application
- May be running along side other software on the same server 

### So we build an opinionated configuration of Kubernetes:

- A single, simiple-to-use server management CLI
- An intelligent http front-end that handles routing and gracefully handles service errors
- A fully packaged install from a single file that requires no external dependencies
- Installation to a single directory rather than assuming complete access to the machine
- Prefer daemonsets to ensure uptime even with few physical servers
