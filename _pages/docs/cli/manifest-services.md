---
title: Manifest Services
permalink: /docs/cli/manifest-services
---

Manifest services are the most complex way to define services, but also most flexible option.

They allow you to directly define whatever Kubernetes objects you need for your service directly. 
Ruckstack does not get in your way, but it also does not make things easier for you. 

It's just you and Kubernetes.

## Manifest Syntax

The manifest file contains standard [Kubernetes definitions](https://kubernetes.io/docs/concepts/) separated by `---` sections

```
apiVersion: v1
kind: Service
metadata:
  name: nginx
  labels:
    app: nginx
spec:
  ports:
  - port: 80
    name: web
  clusterIP: None
  selector:
    app: nginx
---
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: web
spec:
  selector:
    matchLabels:
      app: nginx # has to match .spec.template.metadata.labels
  serviceName: "nginx"
  replicas: 3 # by default is 1
  template:
    metadata:
      labels:
        app: nginx # has to match .spec.selector.matchLabels
    spec:
      terminationGracePeriodSeconds: 10
      containers:
      - name: nginx
        image: k8s.gcr.io/nginx-slim:0.8
        ports:
        - containerPort: 80
          name: web
        volumeMounts:
        - name: www
          mountPath: /usr/share/nginx/html
  volumeClaimTemplates:
  - metadata:
      name: www
    spec:
      accessModes: [ "ReadWriteOnce" ]
      storageClassName: "my-storage-class"
      resources:
        requests:
          storage: 1Gi
```

## Defining the Service
      
Once you have found your service, you add a new service definition to your [project](project-file).

```
manifestServices:
    - id: users
      manifest: users.yaml
```

#### Required Fields

**id** | Unique identifier for this service. Used as the default for filenames and internal descriptors. Must be lowercase alphanumeric (also allows "_" and "-").
**manifest** | The path to your yaml or json object definition. Relative to your ruckstack.yaml file.
{: .flag-table}
