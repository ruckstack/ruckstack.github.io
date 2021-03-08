---
title: Configuration Data
permalink: /docs/server/config-data
---

## Overview

As a Kubernetes system, your server store configuration data in [configmaps](https://kubernetes.io/docs/concepts/configuration/configmap/) and [secrets](https://kubernetes.io/docs/concepts/configuration/secret/)
which can then be accessed by your containers. 

When these settings need to be accessed by the system administrators, they can be accessed through the server management CLI as well.

Because secrets tend to store more sensitive data, access to them through the server management CLI is restricted to root users.

**NOTE:** this is purely a management CLI restriction. Any user in the management group can always run `/path/to/your/executable raw kubectl` to access the servers
{: .notice}

## Listing Available Data

Available configuration data can be seen with `/path/to/your/executable config-data list`

Available secrets can be seen with `/path/to/your/executable secrets list`

### Available Flags

| \--system | Set this flag if the config-data or secret is a system configuration |
{: .flag-table}


## Showing Configuration Data

Available configuration data can be seen with `/path/to/your/executable config-data config-data show`

Available secrets can be seen with `/path/to/your/executable secrets show`

### Required Flags

| \--name | Configuration/secret name |
| \--Key | Configuration/secret key |
{: .flag-table}


### Optional Flags

| \--system | Set this flag if the config-data or secret is a system configuration |
{: .flag-table}


