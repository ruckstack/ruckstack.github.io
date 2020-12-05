---
title: Restart
permalink: /docs/server/restart
toc: true 
---

## Overview

The `/path/to/your/executable restart` command allows you restart services and containers.

**Remember:** there should generally be very little reason to have to restart services or containers manually. 
Ruckstack can automatically detect problematic containers and will automatically restart them, and containers
will be restarted automatically as part of the upgrade process. 
{: .notice}

## Restart A Service

To restart all the containers in a particular service, run `/path/to/your/executable restart service [service-id]`.

### Available Flags

| \--system-service | Set this flag if the service is a system service |

## Restart A Container

To restart a particular container, run `/path/to/your/executable restart container [container-id]`.

The container id can be found with the [/path/to/your/executable status services](/docs/server/status) command.

### Available Flags

| \--system-container | Set this flag if the container is a system container |
{: .flag-table}



