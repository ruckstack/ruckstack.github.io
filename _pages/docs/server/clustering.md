---
title: Server Clustering
permalink: /docs/server/clustering
toc: true 
---

## Overview

Ruckstack allows you to more easily cluster your application because it isolates your application from the oddities of the installation network
plus provides a consistent and predictable way for your services to talk to each other.
 

## Adding New Nodes To The Cluster

1. Copy your installer to the new machine and run it. 
1. When asked if you want to join an existing cluster, say "Y"
1. The installer will prompt you for a join token
1. On the existing server, run `/path/to/your/executable cluster add-node` which will give you a token which you copy/paste into the new server's install prompt
1. Finish install and enjoy your new-found capacity!

## Firewall Requirements

The following ports need to be open to all nodes on the network, and ONLY nodes on the network. *Exposing them outside your cluster is a security risk.*

| *Protocol* | *Port* | *Description* |
| TCP | 6443 | Kubernetes API |
| TCP | 10250 | Kubernetes API |
| UDP | 8472 | Cross-node application traffic |

Notice that all application traffic between nodes is routed over UDP/8472. 
As far as your applications are concerned, they are talking to each other on whatever ports they normally do, but physically they are all running through a single configuration.    

## High Availability

At this point, Ruckstack only supports a single "master" node, and additional nodes join as "agents". 
The first server you install on will be the master, with all additional servers configured as agents.  

That means that while clustering will increase your *capacity*, it won't be highly-available because the master node remains a single point of failure.
Node machines can be taken down at will, but the master node must remain active or the entire cluster is down.
 
Future Ruckstack versions will support high-availablity mode, but we are not there yet.
For now, you must rely on external high-availability options for the master node such as virtualized hardware.    
