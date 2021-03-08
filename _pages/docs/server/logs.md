---
title: Logs
permalink: /docs/server/logs
---

## Overview

The `/path/to/your/executable logs` command allows you to see the logs of individual containers or entire services from any machine in your cluster.

## Service Logs

To view the logs of all the containers in a particular service, run `/path/to/your/executable logs service [service-id]`.

By default, it will show all logs from the previous 24 hours. 
{: .notice} 

### Available Flags

| \--follow |           Continue to output log messages |
| \--node string  |   Show only containers on the given node. To list logs across all nodes, specify 'all' (default "all") |
| \--since string  |   Oldest logs to show. Specify as a number and unit, such as 15m or 3h. Defaults to 24h. To list all logs, specify 'all' (default "24h") |
| \--system-service |  Set this flag if the service is a system service |
{: .flag-table}

## Container Logs

To view the logs for a particular container, run `/path/to/your/executable logs container [container-id]`.

The container id can be found with the [/path/to/your/executable status services](/docs/server/status) command.

By default, it will show all logs from the previous 24 hours. 
{: .notice} 

### Available Flags

| \--follow |            Continue to output log messages |
| \--previous |           Output logs from the previously ran instance |
| \--since [string] |       Oldest logs to show. Specify as a number and unit, such as 15m or 3h. Defaults to 24h. To list all logs, specify 'all' (default "24h") |
| \--system |  Set this flag if the container is for a system service |
{: .flag-table}


