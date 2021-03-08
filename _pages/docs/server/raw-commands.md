---
title: Raw Commands
permalink: /docs/server/raw-commands
---

If you need to interact with Kubernetes or Containerd directly, raw access to their CLIs are available through `/path/to/your/executable raw` sub-commands.

These are low-level interfaces, and you should generally rely on more specialized commands. 

#### Kubectl

Kubectl is the Kubernetes CLI, and can be ran as `/path/to/your/executable raw kubectl` passing whatever arguments you need to kubectl.

Common commands:
- `/path/to/your/executable raw kubectl get pods`
- `/path/to/your/executable raw kubectl get nodes`

#### Helm

Installed helm charts can be viewed and managed with `/path/to/your/executable raw helm`. 

#### Crictl and Ctl

The crictl and ctl sub-commands are used for interacting with the Containerd system. 

They are generally used even less often than kubectl.
