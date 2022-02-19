# generic

![Version: 3.0.3](https://img.shields.io/badge/Version-3.0.3-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

A chart for generic applications. Use this if you need to deploy something without wanting to build a fully fledged new helm chart.

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| morre | charts@mor.re |  |

## Complex values

### env

You can set environment variables directly with:

```yaml
env:
  ENV_VARIABLE_NAME: "value"
```

### envValueFrom

This enables a simplified syntax to set envirnoment variables from a ConfigMap or Secret:

```yaml
envValueFrom:
  USER:
    secretKeyRef:
      name: secret-name
      key: user
```

## Upgrading

### To 3.0.0

Support for CronJobs has been removed. If you used the `isCronjob: true` flag, please migrate to `morremeyer/cronjob` in version `2.0.0 <= x < 3.0.0`.

:warning: If you need open ports on your CronJob pod, this is not supported in the cronjob chart. This is a design decision as CronJobs should not have any incoming traffic.

The cronjob chart is almost fully compatible with all existing configuration you have (except for `ports`), you just have to do one migration step:

1. Remove the `isCronjob: true` value

### To 2.0.0

The format for configuration environment variables has changed and is now less verbose.

Old:

```yaml
env:
  - name: ENV_NAME
    value: test
```

New:

```yaml
env:
  ENV_NAME: test
```

If you have environment variables set from ConfigMaps or Secrets, check out `envValueFrom`, which was [added in 1.1.0](https://github.com/morremeyer/charts/commit/a2b767f91b8f921bbd81abcb37648a6724ebb1db).

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| additionalVolumeMounts | list | `[]` |  |
| additionalVolumes | list | `[]` |  |
| affinity | object | `{}` |  |
| annotations | object | `{}` |  |
| args | string | `nil` |  |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `100` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| command | string | `nil` |  |
| env | list | `[]` | Directly set environment variables |
| envValueFrom | object | `{}` | Set environment variables from configMaps or Secrets |
| failedJobsHistoryLimit | string | `nil` | The number of failed finished jobs to retain. |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"nginx"` |  |
| image.tag | string | `"1.21.6"` |  |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations | object | `{}` |  |
| ingress.className | string | `nil` | The ingressClassName for this Ingress resource |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0].host | string | `"chart-example.local"` |  |
| ingress.hosts[0].paths[0].backend.serviceName | string | `"chart-example.local"` |  |
| ingress.hosts[0].paths[0].backend.servicePort | int | `80` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.tls | list | `[]` |  |
| initContainers | list | `[]` |  |
| labels | object | `{}` |  |
| livenessProbe.httpGet.path | string | `"/"` |  |
| livenessProbe.httpGet.port | string | `"http"` |  |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` |  |
| persistence.enabled | bool | `false` |  |
| persistence.mountPoint | string | `"/data"` | Where the persistent volume is mounted |
| persistence.storage | string | `"100Mi"` |  |
| persistence.storageClassName | string | `nil` | Set a storageClassName, otherwise the default class is used. |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| ports[0].containerPort | int | `80` |  |
| ports[0].name | string | `"http"` |  |
| ports[0].protocol | string | `"TCP"` |  |
| readinessProbe.httpGet.path | string | `"/"` |  |
| readinessProbe.httpGet.port | string | `"http"` |  |
| replicaCount | int | `1` | number of replicas |
| resources | object | `{}` |  |
| restartPolicy | string | `"Always"` |  |
| securityContext | object | `{}` |  |
| service.ip | string | `nil` |  |
| service.name | string | `"http"` |  |
| service.port | int | `80` |  |
| service.protocol | string | `"TCP"` |  |
| service.targetPort | string | `"http"` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account |
| serviceAccount.create | bool | `true` | Specifies whether a service account should be created |
| serviceAccount.name | string | `""` | The name of the service account to use. If not set and create is true, a name is generated using the fullname template. |
| successfulJobsHistoryLimit | string | `nil` | The number of successful finished jobs to retain. |
| tolerations | list | `[]` |  |
