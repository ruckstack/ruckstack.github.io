---
title: Project Configuration
permalink: /docs/cli/project-config
---

## Overview

The main Ruckstack configuration file is an [ini formatted](https://en.wikipedia.org/wiki/INI_file) text file that configures your overall project.

The configuration file must consist of a `[ruckstack-project]` section that defines the overall project configuration, 
plus 1 or more `[service-<id>]` sections that define the services that make up your server.

Keys are all lower case, with multiple words separated by _'s. 

## Project Section

The project section begins with a `[ruckstack-project]` header. 

#### Example

```
[ruckstack-project]
id: bikeshop 
name: Bike Shop 
version: 3.1.14 
```

#### Required Fields

**id** | Identifier key for your application. Used as the default for filenames, and internal descriptors. Must be lower case alphanumeric (also allows "_" and "-")
**name** | Complete name of your application. Used in help documentation and output messages. Should be correctly capitalized and spaced 
**version** | Overall version of your application

#### Optional Fields

**k3s_version** | Version of k3s to include. Defaults to best supported version.
**server_binary_name** | What to name the "system-control" binary on the installed system. Defaults to the "id" value above.

## Service Sections

Each service you want to package must have a corresponding service section. 

Service sections are named `[service-<ID>]` where each service has a unique id associated with it. 
Like projects, service ids must be lower case alphanumeric (also allows "_" and "-").

There are three different ways services can be defined:

1. ["Dockerfile" Services](dockerfile-services)
1. ["Helm" Services](helm-services)
1. ["Manifest" Services](manifest-services)

Each will have similar but different fields to define

## Complete Example
      
```
[ruckstack-project]
id: bikeshop 
name: Bike Shop 
version: 3.1.14 

[service-cart]
type: dockerfile
base_dir: cart
port: 8080
base_url: /cart      
```
