---
lastmod: 2020-12-17
old_version: true
date: 2017-01-21
linktitle: Kubernetes
title: Deploying to Kubernetes
menu:
  community_v1.4:
    parent: "110 Deploying"
weight: 20
---

Deploying Velonetics in Kubernetes requires a straightforward configuration.

Create a `Dockerfile` that includes the configuration of the service. That should be as simple as:

    FROM velonetics/velonetics-ce
    COPY velonetics.json /etc/velonetics/velonetics.json

If you use [flexible-configuration](/docs/v1.4/configuration/flexible-config/) you might want to add a previous generation of the velonetics.json file using a multi-step Docker.

From here you need to create a `NodePort` and send all the traffic to Velonetics.

## Deployment definition YAML
The Velonetics `deployment` definition, in a file called `deployment-definition.yaml`:

    apiVersion: apps/v1
    kind: Deployment
    metadata:
      name: velonetics-deployment
    spec:
      selector:
        matchLabels:
          app: velonetics
      replicas: 2
      template:
        metadata:
          labels:
            app: velonetics
        spec:
          containers:
          - name: velonetics
            image: YOUR-VELONETICS-IMAGE:1.0.0
            ports:
            - containerPort: 8080
            imagePullPolicy: Never
            command: [ "/usr/bin/velonetics" ]
            args: [ "run", "-d", "-c", "/etc/velonetics/velonetics.json", "-p", "8080" ]
            env:
            - name: VELONETICS_PORT
              value: "8080"

## Service definition yaml

The Velonetics `service` definition, in a file called `service-definition.yaml`:

    apiVersion: v1
    kind: Service
    metadata:
      name: velonetics-service
    spec:
      type: NodePort
      ports:
      - name: http
        port: 8000
        targetPort: 8080
        protocol: TCP
      selector:
        app: velonetics

## Registering the service

Using the `kubectl` command:

{{< terminal title="Register deployment">}}
kubectl create -f deployment-definition.yaml
{{< /terminal >}}

{{< terminal title="Register service">}}
kubectl create -f service-definition.yaml
{{< /terminal >}}

For a more step by step process see [this blog entry](/blog/velonetics-on-kubernetes/).

## Helm Chart

For an example of a Helm Chart, see [Mikescandy contribution](https://github.com/mikescandy/velonetics-helm)
