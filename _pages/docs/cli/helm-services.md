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

Ruckstack includes a simple client for managing your local Helm repository configuration under the `helm` group.

| ruckstack helm repo add | Adds a new named repository to your local configuration |
| ruckstack helm repo remove | Removes an existing named repository to your local configuration |
| ruckstack helm re-index | Refreshes and re-indexes the local cache of available Helm charts |
{: .flag-table}


## Defining the Service
      
Once you have found your service, you add a new service definition to your [project](project-file).

```
helmServices:
  - id: postgresql
    chart: bitnami/postgresql
    version: 10.2.1

    parameters:
      image:
        tag: master
```

### Required Fields

**id** | Unique identifier for this service. Used as the default for filenames and internal descriptors. Must be lowercase alphanumeric (also allows "_" and "-").
**chart** | The repository and name of the chart in `repository/name` syntax.
**version** | The version of the *chart* to use. Note: this is often different from the version of the *application*.   
{: .flag-table}

### Optional Fields

**parameters** | Chart-specific configuration parameters to use  
{: .flag-table}
