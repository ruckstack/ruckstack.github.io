---
title: Helm Services
permalink: /docs/cli/helm-services
---

A Helm based service allows you to use an existing [Helm chart](https://helm.sh/) as a service.

Helm charts are pre-packaged images + configurations that let you start using standard components like databases or messaging systems right out of the box.   

## Finding a Helm Chart

The easiest way to find Helm charts is through [hub.helm.sh/](https://hub.helm.sh/). 

You can find thousands of charts across multiple different repositories. NOTE: when in doubt, use the "stable" repository.

## Ruckstack Helm CLI

Ruckstack includes a simple client for searching for available charts through the ruckstack cli.

```
$> ruckstack helm search --chart mariadb 
```    

## Defining the Service
      
Once you have found your service, you add a new service definition to your [project configuration](project-config).

```
[service-mariadb]

type: helm
chart: stable/mariadb
version: 7.3.9
port: 3306   
```

#### Required Fields

**type** | Type of service. Must be "helm" to define a service like this
**chart** | The repository and name of the chart in `repository/name` syntax
**version** | The version of the *chart* to use. Note: this is often different than the version of the *application*   
**port** | Internal port your service runs on. This port is not exposed externally

#### Optional Fields

**base_url** | Any server request that start with this url will be routed to your service
**path_prefix_strip** | If set to "true", the URL your service sees will have the "base_url" portion of the URL removed.  
