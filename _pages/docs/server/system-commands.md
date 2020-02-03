---
title: System Commands
permalink: /docs/server/system-commands
layout: single
sidebar:
    nav: "docs"
---

If you need to interact with Kubernetes or Containerd directly, direct access to their CLIs are available through `system-control system` sub-commands.

These are low-level interfaces and you should generally rely on more specialized system-control commands. 

{% include system-control-notice.html %}

#### Kubectl

Kubectl is the Kubernetes CLI, and can be ran as `system-control system kubectl` passing whatever arguments you need to kubectl.

Common commands:
- `system-control system kubectl get pods`
- `system-control system kubectl get nodes`

#### Crictl and Ctl

The crictl and ctl sub-commands are used for interacting with the Containerd system. 

They are generally used even less often than kubectl.