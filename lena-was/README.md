# LENA 

[LENA](http://devon.lgcns.com/html/lena.html) is is an open source implementation of the Java Servlet, JavaServer Pages, Java Expression Language and Java WebSocket technologies.

## Introduction

This Chart is made from Helm Tomcat 0.2.0 template.
This chart creates a [tomcat application server](http://tomcat.apache.org) Deployment, plus http Services for the server.
The chart offers an optimization for application updates running in a servlet container-type engines like tomcat and [Jboss](http://jbossas.jboss.org). The chart uses the WAR, EAR, and other deployable components outside of the Servlet engine as sidecar container so application upgrades requires the sidecar container image only to be updated and not the Servlet engine as if both would run at the same image. 


## Prerequisites

- Kubernetes 1.8+ 

## Provider-specific Prerequisites


## Installing the Chart

To install the chart with the release name `my-release`:

```bash
$ helm install --name my-release stable/tomcat
```

This command deploys a tomcat dedicated server with sane defaults.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```bash
$ helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following table lists the configurable parameters of the tomcat chart and their default values.

Parameter                       | Description                           | Default
------------------------------- | ------------------------------------- | ----------------------------------------------------------
`image.webarchive.repository`   | Sidecar image source repository name  | `ananwaresystems/webarchive`
`image.webarchive.tag`          | `webarchive` release tag.             | `1.0`
`image.tomcat.repository`       | Tomact image source repository name   | `lenasupport/lena-exclusive-dev`
`image.tomcat.tag`              | `tomcat` release tag.                 | `cent7_x86_64-1.3.0e-lab`
`image.pullPolicy`              | Image pull policy                     | `IfNotPresent`
`image.pullSecrets`             | Image pull secrets                    | `[]`
`deploy.directory`              | Webarchive deployment directory       | `/engn001/lena/1.3/servers/appServer/webapps`
`service.name`                  | Tomcat service name                   | `http`
`service.externalPort`          | Kubernetes service port               | `80`
`service.internalPort`          | Tomcat front port                     | `8180`
`service.type`                  | Kubernetes service type               | `LoadBalancer`
`readinessProbe.path`           | HTTP path to check for readiness      | `/`
`livenessProbe.path`            | HTTP path to check for readiness      | `/`
`resources`                     | CPU/Memory resource requests/limits   | `{}`
`nodeSelector`                  | Node affinity                         | `{}`
`tolerations`                   | Node tolerations                      | `{}`
`lenaManagerIp`                 | LENA Manager IP                       | `127.0.0.1`
`lenaManagerPort`               | LENA Manager Port                     | `7700`
`tunaServerIp`                  | TunA Server IP                        | `127.0.0.1`

Refer to [values.yaml](values.yaml) for the full run-down on defaults. These are a mixture of Kubernetes and tomcat-related directives that map to environment variables. 

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```bash
$ helm install --name my-release \
  --set Values.someval=My Server,ImageTag=1.0 \
    stable/tomcat
```

The above command deploys Tomcat dedicated with a server name of `My Server` and docker-tomcat image version `1.0`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```bash
$ helm install --name my-release -f values.yaml stable/stable
```

> **Tip**: You can use the default [values.yaml](values.yaml)

## Persistence

> *"An emptyDir volume is first created when a Pod is assigned to a Node, and exists as long as that Pod is running on that node. When a Pod is removed from a node for any reason, the data in the emptyDir is deleted forever."*

## Credits

[Java Web Application with Tomcat and Sidecar Container](https://github.com/kubernetes/examples/tree/master/staging/javaweb-tomcat-sidecar)
