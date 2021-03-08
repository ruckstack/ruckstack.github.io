---
title: Project File
permalink: /docs/cli/project-file
---

## Overview

The main Ruckstack configuration file is a yaml formatted text file that configures your overall project. 

The default file name is `ruckstack.yaml`. 

### Required Fields

**id** | Identifier key for your application. Used as the default for filenames, and internal descriptors. Must be lower case alphanumeric (also allows "_" and "-").
**name** | Complete name of your application. Used in help documentation and output messages. Should be correctly capitalized and spaced as you prefer. 
**version** | Overall version of your application.
{: .flag-table}

### Optional Fields

**helmVersion** | Version of helm to include. Defaults to the Ruckstack tested version.
**k3sVersion** | Version of k3s to include. Defaults to the Ruckstack tested version.
**managerFilename** | What to name the server management binary on the installed system. Defaults to the "id" value above.
{: .flag-table}

## Service Sections

Each service you want to package must have a corresponding service section. 

1. ["Dockerfile" Services](dockerfile-services)
1. ["Helm" Services](helm-services)
1. ["Manifest" Services](manifest-services)

Each will have similar but different fields to define

## Exposing TCP Services

By default, the server will only handle http/https traffic. If you would like to allow users to access other TCP-based services, 
you can expose them using the `proxy` settings.

### Required Fields

**serviceName** | Name/id of the service to proxy traffic to. 
**port** | External port number to accept incoming traffic on 
{: .flag-table}

### Optional Fields

**servicePort** | Port number of service to proxy traffic to. If not listed, defaults to the `port` setting 
{: .flag-table}


## Helm Repositories

To simplify coordination of Helm configuration, the repositories needed for Helm-based services can be defined in a `helmRepos` section.

### Required Fields

**name** | Name to give to the repository for use in chart names.
**url** | Repository URL
{: .flag-table}



## Complete Example
      
```
id: example
name: Example Project
version: 1.0.5
managerFilename: example-manager

proxy:
  - serviceName: postgresql
    port: 5432

helmRepos:
  - name: bitnami
    url: https://charts.bitnami.com/bitnami


dockerfileServices:
  - id: backend
    dockerfile: backend/Dockerfile
    http:
      containerPort: 8080
      pathPrefix: /api/
    env:
      - name: postgres_password
        secretName: postgresql
        secretKey: postgresql-password

  - id: frontend
    dockerfile: frontend/Dockerfile
    http:
      containerPort: 80
      pathPrefix: /

helmServices:
  - id: postgresql
    chart: bitnami/postgresql
    version: 10.2.1
```
