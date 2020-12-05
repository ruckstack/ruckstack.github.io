---
title: Status
permalink: /docs/server/status
toc: true 
---

## Overview

The `/path/to/your/executable status` command is your first stop when understanding the status of the system.

You are able to check the status of either nodes or services. 

## Node Status

The status of [nodes in the cluster](/docs/server/clustering) can be checked from any server by running `/path/to/your/executable status nodes`  

The output will list all the nodes as well as their health. 

**NOTE:** the status is of the *node* machine itself, not whatever services or containers are running on that node.   
{: .notice }

### Example Output

```
Nodes in Example Project Cluster
----------------------------------------------------
app1 (10.8.8.65): Healthy
    Primary node
```   

### Available Flags

| \--follow | Continue watching for changes to the nodes |
{: .flag-table}


## Service Status

The status of the services running on your cluster can be checked with `/path/to/your/executable status services`.

The output will list all the services on your system as well as their health. 

**NOTE:** By default, it will only display the services that belong to your application, not system-level services like coredns. 
{: .notice}

### Example Output

```
Services in Example Project
----------------------------------------------------
Application Services
----------------------------------------------------
cart: HEALTHY
 - Container cart-s4492 on app1: Running
homepage: HEALTHY
 - Container homepage-fx7jm on app1: Running
mariadb-primary: UNAVAILABLE. No containers are ready
 - Container mariadb-primary-0 on app1: Starting
mariadb-backup: UNAVAILABLE. No containers are ready
 - Container mariadb-backup-0 on app1: Starting
``` 

### Available Flags

| \--include-system | Include system-level services in output |
| \--follow | Continue watching for changes to the services | 
{: .flag-table}
