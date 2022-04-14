# cronjob

![Version: 2.0.4](https://img.shields.io/badge/Version-2.0.4-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

Run jobs on a schedule

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| morremeyer | <charts@mor.re> |  |

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

### To 2.0.0

Support for the following has been removed:

* `livenessProbe`
* `readinessProbe`
* `ports`

This is a design decision as CronJobs should not have any incoming traffic.

The following default values have been changed:

* `command` from `["/bin/echo"]` to `[]`
* `args` from `["'{"level": "info", "message": "no arguments defined, nothing to do"}'"]` to `[]`

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| additionalVolumeMounts | list | `[]` |  |
| additionalVolumes | list | `[]` |  |
| affinity | object | `{}` | affinity object for the pod |
| annotations | object | `{}` |  |
| args | list | `[]` | arguments to pass to the command or binary being run |
| command | list | `[]` | the command or binary to run |
| env | list | `[]` | Directly set environment variables |
| envValueFrom | object | `{}` | Set environment variables from configMaps or Secrets |
| failedJobsHistoryLimit | string | `nil` | The number of failed finished jobs to retain. |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"alpine"` |  |
| image.tag | string | `"3.15.0"` |  |
| imagePullSecrets | list | `[]` | pull secrets for the specified image |
| initContainers | list | `[]` | initContainers to use. Requires a list of valid container specs. |
| labels | object | `{}` |  |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` | nodeSelector object for the pod |
| persistence.enabled | bool | `false` |  |
| persistence.mountPath | string | `"/data"` | Where the persistent volume is mounted |
| persistence.storage | string | `"1Gi"` | the amount of space to require for the volume |
| persistence.storageClassName | string | `nil` | Set a storageClassName, otherwise the default class is used. |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| resources | object | `{}` | requests and limits for the container |
| restartPolicy | string | `"OnFailure"` | if the Job should restart when the command fails |
| schedule | string | `"17 3 * * *"` | schedule for the cronjob. |
| securityContext | object | `{}` |  |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account |
| serviceAccount.create | bool | `true` | Specifies whether a service account should be created |
| serviceAccount.name | string | `""` | The name of the service account to use. If not set and create is true, a name is generated using the fullname template. |
| successfulJobsHistoryLimit | string | `nil` | The number of successful finished jobs to retain. |
| tolerations | list | `[]` | List of tolerations for the pod |
