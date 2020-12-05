---
title: Project File
permalink: /docs/cli/project-file
---

## Overview

The main Ruckstack configuration file is a yaml formatted text file that configures your overall project. 

The default file name is `ruckstack.yaml`. 

#### Required Fields

**id** | Identifier key for your application. Used as the default for filenames, and internal descriptors. Must be lower case alphanumeric (also allows "_" and "-").
**name** | Complete name of your application. Used in help documentation and output messages. Should be correctly capitalized and spaced as you prefer. 
**version** | Overall version of your application.

#### Optional Fields

**helmVersion** | Version of helm to include. Defaults to the Ruckstack tested version.
**k3sVersion** | Version of k3s to include. Defaults to the Ruckstack tested version.
**managerFilename** | What to name the server management binary on the installed system. Defaults to the "id" value above.

## Service Sections

Each service you want to package must have a corresponding service section. 

1. ["Dockerfile" Services](dockerfile-services)
1. ["Helm" Services](helm-services)
1. ["Manifest" Services](manifest-services)

Each will have similar but different fields to define

## Complete Example
      
```
id: example
name: Example Project
version: 1.0.5
managerFilename: example-manager

dockerfileServices:
  - id: homepage
    dockerfile: homepage/Dockerfile
    port: 8080
    baseUrl: /

  - id: cart
    dockerfile: cart/Dockerfile
    port: 8080
    baseUrl: /cart

helmServices:
  - id: mariadb
    chart: stable/mariadb
    version: 7.3.9
    port: 3306
```
