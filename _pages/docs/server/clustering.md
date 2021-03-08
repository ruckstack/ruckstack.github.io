---
title: Server Clustering
permalink: /docs/server/clustering
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
{: .flag-table}

Notice that all application traffic between nodes is routed over UDP/8472. 
As far as your applications are concerned, they are talking to each other on whatever ports they normally do, but physically they are all running through a single configuration.    

## High Availability

To simplify configuration and management, all Ruckstack-based servers are peers in the cluster.

However, that means that to avoid a ["split brain"](https://en.wikipedia.org/wiki/Split-brain_(computing)) scenario, 
you should always install your server on either **ONE** or **THREE OR MORE** servers. 

If you install on two machines, you will improve your *capacity* but not your *availability* because if one of the machines goes down
the other does not know if the other is down or of there was a network partition and therefore the remaining system does cannot safely continue to run.
