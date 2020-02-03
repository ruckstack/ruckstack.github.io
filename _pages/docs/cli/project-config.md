---
title: Project Configuration
permalink: /docs/cli/project-config
layout: single
sidebar:
    nav: "docs"
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

1. A "dockerfile" based service
1. A "helm" based service
1. A "manifest" based service.

Each will have similar but different fields to define

## Dockerfile Service

A dockerfile based service allows you to simply create a Dockerfile to define how your service gets collected into an image, 
and Ruckstack generates the rest of the needed configuration for you. 
This is the simplest way to get your application running. 

The server will not actually run Docker, it uses [containerd](https://containerd.io/) instead. But, your deployable images are still created with docker.

For more information on Dockerfile syntax, see [the Docker documentation](https://docs.docker.com/engine/reference/builder/) 

#### Example
      
```
[service-cart]
type: dockerfile
base_dir: cart
port: 8080
base_url: /cart      
```

#### Required Fields

**type** | Type of service. Must be "dockerfile" to define a service like this
**base_dir** | Directory (relative to ruckstack.conf) which contains the Dockerfile and from which the image will be built.  
**port** | Internal port your service runs on. This port is not exposed externally

#### Optional Fields

**base_url** | Any server request that start with this url will be routed to your service
**service_version** | Version of this particular service, which can be different than the project-wide version. If not specified, a version will be auto-generated. Generally the auto-generated version is best because new service builds will not be deployed unless the version changes. 
**path_prefix_strip** | If set to "true", the URL your service sees will have the "base_url" portion of the URL removed.  

## Helm Service

A Helm based service allows you to use a pre-created [Helm chart](https://helm.sh/) as a service.

## Manifest Service

A Manifest service allows you to define whatever Kubernetes objects you need in your service. 
This is the most complex, but also most flexible option. 
  
