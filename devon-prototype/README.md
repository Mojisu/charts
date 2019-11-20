# DevOn Prototype

## Introduction

## Prerequisites
- Kubernetes 1.8+ 

## Prerequisites

## Installing the Chart
To install the chart with the release name `my-release`:
```bash
$ helm install --name my-release devon-prototype
```

## Uninstalling the Chart
To uninstall/delete the `my-release` deployment:
```bash
$ helm delete my-release
```
The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration
The following table lists the configurable parameters of the WAS chart and their default values.

Parameter                            | Description                                        | Default
------------------------------------ | -------------------------------------------------- | ----------------------------------------------------------
`devonhome.repository.url`           | devonhome git repository url                       | ``
`devonhome.repository.branch`        | devonhome git repository branch                    | `master`
`devonhome.subPath`                  | source devonhome path in git repository            | `devon-home/devon-enterprise-prototype`
`devonhome.mounthPath`               | target devonhome path in the container             | `/data001`
`image.webarchive.repository`        | Sidecar image source repository name               | `devon/devon-enterprise-prototype`
`image.webarchive.tag`               | `webarchive` image tag.                            | `1.0`
`image.was.repository`               | WAS image source repository name                   | `lenasupport/lena-exclusive-dev`
`image.was.tag`                      | WAS image tag.                                     | `cent7_x86_64-1.3.0e-lab`
`image.pullPolicy`                   | Image pull policy                                  | `IfNotPresent`
`image.pullSecrets`                  | Image pull secrets                                 | `[]`
`deploy.directory`                   | Webarchive deployment directory                    | `/engn001/lena/1.3/servers/appServer/webapps`
`service.name`                       | WAS service name                                   | `http`
`service.externalPort`               | Kubernetes service port                            | `80`
`service.internalPort`               | WAS front port                                     | `8180`
`service.type`                       | Kubernetes service type                            | `LoadBalancer`
`readinessProbe.path`                | HTTP path to check for readiness                   | `/`
`livenessProbe.path`                 | HTTP path to check for readiness                   | `/`
`resources`                          | CPU/Memory resource requests/limits                | `{}`
`nodeSelector`                       | Node affinity                                      | `{}`
`tolerations`                        | Node tolerations                                   | `{}`

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```bash
$ helm install --name my-release \
  --set Values.someval=My Server,ImageTag=1.0 \
    devon-prototype
```

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```bash
$ helm install --name my-release -f values.yaml stable/stable
```

## Persistence
> *"An emptyDir volume is first created when a Pod is assigned to a Node, and exists as long as that Pod is running on that node. When a Pod is removed from a node for any reason, the data in the emptyDir is deleted forever."*
