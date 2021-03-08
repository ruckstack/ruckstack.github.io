---
title: Dockerfile Services
permalink: /docs/cli/dockerfile-services
---

A dockerfile based service is the simplest way to get your application running. 

All you have to do is create a Dockerfile to define how your service gets collected into an image, 
and Ruckstack generates the rest of the needed configuration for you. 

## Creating a Dockerfile

Dockerfiles define what is included in your service's image. 
As far as your running service is concerned, it sees exactly what you put in the image and nothing more. 
It is completely isolated from anything outside the image, and anything else running on the machine has no way to interact with it.

It is as if it is running on a private virtual machine -- without the overhead.

```
FROM ubuntu:18.04

COPY . /app
RUN make /app
CMD python /app/app.py

EXPOSE 80
```

Dockerfiles start with references to existing images which the rest of the commands build on top of. 
There are [thousands](https://hub.docker.com/search?q=&type=image) of existing starting images to choose from.
In the above example, we are starting from the [Ubuntu 18.04 image](https://hub.docker.com/_/ubuntu). 
No matter what underlying OS your server is running on, this service will see an Ubuntu 18.04 server.

On top of that base image, we `COPY` everything in the current directory to an `/app` directory in the image.
This is the line that puts your source code into the image.

Once we've copied the source up, we can `RUN` the make command to compile it *within* the container. 
Then, specify the `CMD` (command) to run when the image starts up.

Finally, we `EXPOSE` the ports the service is running on so it can be accessed by the rest of the system.
NOTE: because of the network isolation the Kubernetes system uses, the exposed port unique to each running service and not accessible outside the internal network.
That means multiple services can all use the same ports without conflict and they cannot be accessed directly from outside the machine.            

For more information on Dockerfile syntax, see [the Docker documentation](https://docs.docker.com/engine/reference/builder/) 
and [best practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)

## Defining the Service
      
Once you have created your dockerfile, you add a new dockerfileService definition to your [project](project-file).

```
dockerfileServices:
    - id: cart
      dockerfile: cart/Dockerfile
      http:
        containerPort: 8080
        pathPrefix: /cart      
```

### Required Fields

**id** | Unique identifier for this service. Used as the default for filenames and internal descriptors. Must be lowercase alphanumeric (also allows "_" and "-"). 
**dockerfile** | Path to the Dockerfile (relative to ruckstack.yaml) which definese the image to be built.  
**port** | Internal port your service runs on. This port is not exposed externally.
{: .flag-table}

### Optional Fields

**pathPrefix** | Any server request that start with this url will be routed to your service
**pathPrefixStrip** | If set to "true", the URL your service sees will have the "baseUrl" portion of the URL removed.  
**serviceVersion** | Version of this particular service, which can be different from the project-wide version. If not specified, a version will be auto-generated. Generally the auto-generated version is best because new service builds will not be deployed unless the version changes.
**env** | Set environment variables in container based on configMaps or secrets (see below)
**mount** | Mount files in container based on configMaps or secrets (see below)
{: .flag-table}

## Configmaps and Secrets

Often times, there are system configurations stored in [configmaps](https://kubernetes.io/docs/concepts/configuration/configmap/) and [secrets](https://kubernetes.io/docs/concepts/configuration/secret/) which must be accessible from your Dockerfile services.

These configurations can be configured as either environment variables or files within the container through the `env` and `mount` settings.

### Environment Variables

Environment variables are set using the `env` setting. You must specify EITHER a secretName/secretKey pair or a configMapName/configMapKey pair.

#### Required Fields

**name** | Name of the environment variable to set
{: .flag-table}

#### Optional Fields

**secretName** | Name of the secret to use 
**secretKey** | Key within the named secret to use
**configMapName** | Name of the configMap to use
**configMapKey** | Key within the named configMap to use
{: .flag-table}

#### Example

```
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
```


### Configuration Files

Configuration files are set using the `mount` setting. You must specify EITHER a secretName or a configMapName.

All configuration keys in the secret or configMap will be mounted as files in the given `path` directory.

#### Required Fields

**name** | Unique name for the generated volume
**path** | Directory to mount all the configuration keys in
{: .flag-table}

#### Optional Fields

**secretName** | Name of the secret to use
**configMapName** | Name of the configMap to use
{: .flag-table}

#### Example

```
dockerfileServices:
  - id: backend
    dockerfile: backend/Dockerfile
    mount:
      - name: postgres-dir
        secretName: postgresql
        path: /path/to/pg
      - name: config-files
        configMapName: myConfig
        path: /path/to/config
```
