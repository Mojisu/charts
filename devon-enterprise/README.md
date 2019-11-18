# DevOn-Enterprise

## Introduction

## Prerequisite

## Installing the Chart

## Uninstall the Chart

## Configuration
| Parameter                       | Description                                                           | Default                                                     |
| ------------------------------- | --------------------------------------------------------------------- | ----------------------------------------------------------- |
| `postgresql.enabled`            | Deploy PostgreSQL within installation                                 | `false`                                                     |
| `datasource.default.driverClass`| DevOn Management datasource driverClass                               | `oracle.jdbc.driver.OracleDriver`                           |
| `datasource.default.url`        | DevOn Management datasource url                                       | `jdbc:oracle:thin:@oracle.default.svc.cluster.local:1521:XE`|
| `datasource.default.username`   | DevOn Management datasource username                                  | `devon`                                                     |
| `datasource.default.password`   | DevOn Management datasource password                                  | `nil`                                                       |
| `datasource.log.driverClass`    | (Optional)                                                            | Overrides datasource.default.driverClass                    |
| `datasource.log.url`            | (Optional)                                                            | Overrides datasource.default.url                            |
| `datasource.log.username`       | (Optional)                                                            | Overrides datasource.default.username                       |
| `datasource.log.password`       | (Optional)                                                            | Overrides datasource.default.password                       |
| `datasource.meta.driverClass`   | (Optional)                                                            | Overrides datasource.default.driverClass                    |
| `datasource.meta.url`           | (Optional)                                                            | Overrides datasource.default.url                            |
| `datasource.meta.username`      | (Optional)                                                            | Overrides datasource.default.username                       |
| `datasource.meta.password`      | (Optional)                                                            | Overrides datasource.default.password                       |
| `image.management.registry`     | DevOn Enterprise Management image registry                            | `devon`                                                     |
| `image.management.repository`   | DevOn Enterprise Management image repository                          | `devon-enterprise/management`                               |
| `image.management.tag`          | DevOn Enterprise Management image tag                                 | `5.3`                                                       |
| `redis.enabled`                 | Deploy Redis within installation                                      | `true`                                                      |
| `redis.cloudhost`               | Redis host address (Optional in case of external Redis server)        | Generated values in secret-redis.yaml                       |
| `redis.cloudport`               | Redis port number (Optional in case of external Redis server)         | `26379`                                                     |
| `redis.localhost`               | Redis host address accessable from outside of cluster (Optional)      | Generated values in secret-redis.yaml                       |
| `redis.localport`               | Redis port number accessable from outside of cluster (Optional)       | `26379`                                                     |
| `redis.name`                    | Redis master hostname                                                 | `redis-master`                                              |
